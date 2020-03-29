# LogEpi
LogEpi: Logistic curves applied to epidemiology

So far, this package contains three main functions:
mkEpiTables
mkEpiCurves
yhat

The Covid-19 data that motivated this package and is used in the examples is available at the European Centre for Disease Prevention and Control (https://www.ecdc.europa.eu/en/publications-data/download-todays-data-geographic-distribution-covid-19-cases-worldwide).

The Covid-19_vignette.pdf offers a brief explanation of how the logistic curve is used to model epidemiological events, and provides a set of examples.

To load this data directly into R, follow the code below:

info.url <- paste("https://www.ecdc.europa.eu/sites/default/files/documents/COVID-19-geographic-disbtribution-worldwide-",format(Sys.time(),"%Y-%m-%d"),".xlsx",sep="")
GET(info.url,authenticate(":",":",type="ntlm"),write_disk(tf <- tempfile(fileext=".xlsx")))
info <- as.data.frame(read_excel(tf))[,-1]
names(info)[6] <- "Countries.and.territories"
