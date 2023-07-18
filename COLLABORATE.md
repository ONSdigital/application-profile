# Collaborate with Integrated Data Service Dissemination

You've decided to collaborate with the Integrated Data Service Dissemination (IDSD) project. Great! We're excited to have you on board. The way you do this is by preparing a CSV-W and publishing it online. There are many ways of doing this, but we recommend using our tooling to speed up the generation and markup of the [CSV-W](CSV-on-the-Web). We are targetting UK Government departments, offices, and agencies, but if there is a compelling case you can still ask to contribute to our Linked Data Store, [Integrated Data Service Data Explorer](https://beta.gss-data.org.uk/).

## Our services

The IDS Dissemination Service has a number of offering surrounding the disseminiation of linked data. There are no one size fits all solutions, so we will work with you to find the best solution for your data. We can:

*   Consult on your data and how to get it in the best shape for publication
*   Consult on your metadata, taxinomies, and code lists to align with best practise and standard vocabularies
*   Ingest your data into our [Linked Data Store](https://beta.gss-data.org.uk/) from CSV-W
*   Provide reviews of first publications to ensure that your team is best placed to embrace linked data

## Consulting on Data

We can provide advice on how to get your data in the best shape for publication. At a minimum we start by getting the data into a tidy, observational shape cherished by analysts everywhere. From this point you're leaving the world of spreadsheets behind.

## Consulting on Metadata, Taxonomies, and Code Lists

Linked data is all about the relationships between things. We can help you to align your metadata, taxonomies, and code lists with standard vocabularies and best practise. This will ensure that your data is Findable, Accessible, Interoperable, and Reusable. We can also help you to align your data with the [Central Digital & Data Office standards for describing CSVs with Metadata](https://www.gov.uk/government/publications/recommended-open-standards-for-government/using-metadata-to-describe-csv-data).

The highest benefit for adopting linked data comes from reusing existing taxonomies. We can help you to find existing taxonomies and vocabularies that you can use to describe your data. The two main taxonomies which provide the most benefit are the [ONS Statistical Geographies](https://www.ons.gov.uk/methodology/geography), and observational [Time Period Notation](https://github.com/epimorphics/IntervalServer/blob/master/interval-uris.md).

### Adopting the ONS Statistical Geographies

Adopting ONS Statistical Geographies brings statistical discoverability to the publics' desire to learn about their local area. It also brings the benefit of being able to compare data across different geographies. Using our tooling, namely [csvcubed](https://gss-cogs.github.io/csvcubed-docs/external/), you can easily adopt the ONS Statistical Geographies by using a template in your metadata markup file referencing a column in your CSV using the codes you might already be familiar with (e.g. `N09000010` representing the Northern Ireland county of Newry, Mourne and Down).

```csv
STATISTIC CODE,Statistic,TLIST(A1),Year,LGD2014,Local Government District,VALUE
ART,"Ambulance response time, median",2010,2010,N09000001,Antrim and Newtownabbey,442
ART,"Ambulance response time, median",2010,2010,N09000002,"Armagh City, Banbridge and Craigavon",429
...
ART,"Ambulance response time, median",2010,2010,N09000010,"Newry, Mourne and Down",431
```

```json
...
        "LGD2014": {
            "from_template": "statistical-geography"
        },
...
```

### Adopting Time Period Notation

Adopting Time Period Notation brings the benefit of being able to ensure you are comparing observations from the same time periods. Using our tooling, namely [csvcubed](https://gss-cogs.github.io/csvcubed-docs/external/), you can easily adopt Time Period Notation by using a template in your metadata markup file referencing a column in your CSV using the codes you might already be familiar with (e.g. `2010-Q1` representing the first quarter of 2010).

```csv
STATISTIC CODE,Statistic,TLIST(A1),Year,LGD2014,Local Government District,VALUE
ART,"Ambulance response time, median",2010,2010,N09000001,Antrim and Newtownabbey,442
ART,"Ambulance response time, median",2010,2010,N09000002,"Armagh City, Banbridge and Craigavon",429
...
ART,"Ambulance response time, median",2010,2010,N09000010,"Newry, Mourne and Down",431
```

```json
...
        "Year": {
            "from_template": "year"
        },
...
```

### Measures & Units

We can also help you align your data to standardised measures and units. It's important that measures are well defined without units included in the name, that indecies are correctly expressed, and that related measures can be found quickly using a hierarchy of measures. Expressing measures correctly requires practise, and we can continue to help you adopt the best practise as you publish your statistics.

Units are a bit easier. Most official, national, and experimental statistics use common units like numbers, percentages, currency, time, and distance. Reusing existing units from the [QUDT Unit Vocabulary](https://qudt.org/2.1/vocab/unit) and extending them when talking about multiples is easier when figuring out how to express the measure discretely. 

e.g. Pounds Sterling and Millions of Pounds Sterling are related and convertable between the two.

Expressing indecies requires the inclusion of a base year, but we can help with that too.

### Other Statistical Components

Many data publications across government include confidence and credible intervals, non-seasonal and seasonally adjusted data, and supression of observations to prevent disclosure of confidential data. Our tooling can help you to express these components in your metadata, and we can consult on how best to express your data faithfully that is both machine and human readable.

## Ingesting your data into our Linked Data Store

We can ingest your data into [IDS Data Explorer](https://beta.gss-data.org.uk/) from CSV-W stored anywhere on the internet. We can also assit on you publishing your CSV-Ws in an accesible location for us access and add to our service. 

In the future we will support users annoucing the publication of their data via an API so that the ingestion becomes a fully automated process.

## Reviewing your first publication ... and beyond

We can review your first publication to ensure that your team has adopted the minimum standards of FAIR data. We can also provide advice on next steps, or continue to collaborate with so that you can continue to improve your data on your own.

To find out more about how we review data, please see our review process. It is applicable to all data published on the [IDS Data Explorer](https://beta.gss-data.org.uk/), regardless of source.

## Get in touch

If you're interested in any of the services we offer, please get in touch with us at [idps.dissemination@ons.gov.uk](mailto:idps.dissemination@ons.gov.uk).