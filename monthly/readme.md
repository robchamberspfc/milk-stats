
## Steps

Transform file (TBC)
- [Create tidy CSV](https://github.com/robchamberspfc/table-to-tidy-csv)
- [Transform to RDF using table2qb](https://github.com/Swirrl/table2qb)


### Create catalogue entry

1. Create new Draft in PMD (named anything - only lasts until published)
2. Go to Dataset tab and Click `Add new dataset`
3. Update identifier to `http://environment.data.gov.uk/linked-data/data/milk-prices-monthly-catalogue-entry`
4. Add title `Milk prices (monthly)`
5. Add licence `http://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/`
6. Save

### Create Dataset

1. Go to Edit
2. In `Add data` section select `choose file` and upload [cube.ttl](data/cube.ttl)
3. Click `Add data to entry`
4. You will be taken to `Job in progress` screen
5. Once complete go back to edit screen and `Change type` to `DataCube`
6. Click `Change type of entry` to save

### Upload components

1. Go to Reference (should this be vocabularies?)
2. Click Add new reference
3. Add title `Milk prices (monthly) components`
4. Add licence `http://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/`
5. Go to Edit
6. In `Add data` section select `choose file` and upload [components.ttl](data/components.ttl)
7. Click `Add data to entry`
8. Once complete go back to edit screen and `Change type` to `Ontology`
9. Click `Change type of entry` to save

### Upload temporary extra labels

1. Go to Reference (should this be vocabularies?)
2. Click Add new reference
3. Add title `Temporary extra labels`
4. Add licence `http://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/`
5. Go to Edit
6. In `Add data` section select `choose file` and upload [temporary-labels.ttl](data/temporary-labels.ttl)
7. Click `Add data to entry`

### Publish draft

1. In header bar click icon next to your draft name
2. In Actions select `Publish {your draft name}`




## To make cube (WiP)

Need to run a SPARQL update to manually to a step 
PMD doesn't do automatically yet

```
PREFIX dc: <http://purl.org/dc/elements/1.1/>
DELETE DATA
{ GRAPH <http://environment.data.gov.uk/graph/milk-prices-monthly-metadata> { <http://environment.data.gov.uk/linked-data/data/milk-prices-monthly-catalogue-entry>  <http://publishmydata.com/pmdcat#datasetContents>  <http://environment.data.gov.uk/graph/milk-prices-monthly> } } ;

INSERT DATA
{ GRAPH <http://environment.data.gov.uk/graph/milk-prices-monthly-metadata> { <http://environment.data.gov.uk/linked-data/data/milk-prices-monthly-catalogue-entry>  <http://publishmydata.com/pmdcat#datasetContents>  <http://environment.data.gov.uk/linked-data/data/milk-prices-monthly> .
                                                                            <http://environment.data.gov.uk/linked-data/data/milk-prices-monthly> <http://www.w3.org/1999/02/22-rdf-syntax-ns#type> <http://publishmydata.com/pmdcat#DataCube>}}
