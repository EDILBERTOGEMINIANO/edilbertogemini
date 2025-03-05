let
    Source = Excel.Workbook(File.Contents("C:\Users\Computer LAB\Downloads\Uncleaned_DS_jobs.xlsx"), null, true),
    Uncleaned_DS_jobs_Sheet = Source{[Item="Uncleaned_DS_jobs",Kind="Sheet"]}[Data],
    #"Promoted Headers" = Table.PromoteHeaders(Uncleaned_DS_jobs_Sheet, [PromoteAllScalars=true]),
    #"Changed Type" = Table.TransformColumnTypes(#"Promoted Headers",{{"index", Int64.Type}, {"Job Title", type text}, {"Salary Estimate", type text}, {"Job Description", type text}, {"Rating", type number}, {"Company Name", type text}, {"Location", type text}, {"Headquarters", type any}, {"Size", type any}, {"Founded", Int64.Type}, {"Type of ownership", type any}, {"Industry", type any}, {"Sector", type any}, {"Revenue", type any}, {"Competitors", type any}}),
    #"Extracted Text Before Delimiter" = Table.TransformColumns(#"Changed Type", {{"Salary Estimate", each Text.BeforeDelimiter(_, "("), type text}}),
    #"Inserted Text Between Delimiters" = Table.AddColumn(#"Extracted Text Before Delimiter", "MinSal", each Text.BetweenDelimiters([Salary Estimate], "$", "K"), type text),
    #"Reordered Columns" = Table.ReorderColumns(#"Inserted Text Between Delimiters",{"index", "Job Title", "MinSal", "Salary Estimate", "Job Description", "Rating", "Company Name", "Location", "Headquarters", "Size", "Founded", "Type of ownership", "Industry", "Sector", "Revenue", "Competitors"}),
    #"Inserted Text Between Delimiters1" = Table.AddColumn(#"Reordered Columns", "MaxSal", each Text.BetweenDelimiters([Salary Estimate], "$", "K", 1, 0), type text),
    #"Reordered Columns1" = Table.ReorderColumns(#"Inserted Text Between Delimiters1",{"index", "Job Title", "MinSal", "MaxSal", "Salary Estimate", "Job Description", "Rating", "Company Name", "Location", "Headquarters", "Size", "Founded", "Type of ownership", "Industry", "Sector", "Revenue", "Competitors"}),
    #"Removed Columns" = Table.RemoveColumns(#"Reordered Columns1",{"Salary Estimate"}),
    #"Added Custom" = Table.AddColumn(#"Removed Columns", "Role Type ", each if Text.Contains([Job Title], "Data Scientist") then
"Data Scientist"
else if Text.Contains([Job Title], "Data Analyst") then
"Data Analyst"
else if Text.Contains([Job Title], "Data Engineer") then
"Data Engineer"
else if Text.Contains([Job Title], "Machine Learning") then
"Machine Learning Engineer"
else
"other"),
    #"Reordered Columns2" = Table.ReorderColumns(#"Added Custom",{"index", "Job Title", "Role Type ", "MinSal", "MaxSal", "Job Description", "Rating", "Company Name", "Location", "Headquarters", "Size", "Founded", "Type of ownership", "Industry", "Sector", "Revenue", "Competitors"}),
    #"Added Custom1" = Table.AddColumn(#"Reordered Columns2", "Custom", each if [Location]= "New Jersey" then ", NJ"
else if [Location] = "Remote" then ", other"
else if [Location]= "United States" then ", other"
else if [Location]= "Texas" then ", TX"
else if [Location]= "Patuxent" then ", MA"
else if [Location]= "California" then ", CA"
else if [Location]= "Utah" then ", UT"
else [Location]),
    #"Reordered Columns3" = Table.ReorderColumns(#"Added Custom1",{"index", "Job Title", "Role Type ", "MinSal", "MaxSal", "Job Description", "Rating", "Company Name", "Location", "Custom", "Headquarters", "Size", "Founded", "Type of ownership", "Industry", "Sector", "Revenue", "Competitors"}),
    #"Split Column by Delimiter" = Table.SplitColumn(#"Reordered Columns3", "Custom", Splitter.SplitTextByDelimiter(",", QuoteStyle.Csv), {"Custom.1", "Custom.2"}),
    #"Changed Type1" = Table.TransformColumnTypes(#"Split Column by Delimiter",{{"Custom.1", type text}, {"Custom.2", type text}}),
    #"Replaced Value" = Table.ReplaceValue(#"Changed Type1"," Anne Arundel","MA",Replacer.ReplaceText,{"Custom.2"}),
    #"Split Column by Delimiter1" = Table.SplitColumn(#"Replaced Value", "Size", Splitter.SplitTextByDelimiter("to ", QuoteStyle.Csv), {"Size.1", "Size.2"}),
    #"Changed Type2" = Table.TransformColumnTypes(#"Split Column by Delimiter1",{{"Size.1", type text}, {"Size.2", type text}}),
    #"Renamed Columns" = Table.RenameColumns(#"Changed Type2",{{"Size.1", "MinCompanySize"}, {"Size.2", "MaxCompanySize"}}),
    #"Changed Type3" = Table.TransformColumnTypes(#"Renamed Columns",{{"Competitors", type text}}),
    #"Replaced Value1" = Table.ReplaceValue(#"Changed Type3","-1","N/A",Replacer.ReplaceText,{"Competitors"}),
    #"Changed Type4" = Table.TransformColumnTypes(#"Replaced Value1",{{"Revenue", type text}}),
    #"Changed Type5" = Table.TransformColumnTypes(#"Changed Type4",{{"Industry", type text}}),
    #"Replaced Value3" = Table.ReplaceValue(#"Changed Type5","-1","other",Replacer.ReplaceText,{"Industry"}),
    #"Replaced Value2" = Table.ReplaceValue(#"Replaced Value3","-1","OTHER",Replacer.ReplaceText,{"Industry"}),
    #"Filtered Rows" = Table.SelectRows(#"Replaced Value2", each true),
    #"Replaced Value4" = Table.ReplaceValue(#"Filtered Rows","-1","0",Replacer.ReplaceText,{"Revenue"})
in
    #"Replaced Value4"
