# Master Measures Guide

This is the official Qlik Sense API documentation. It could be used as a reference for understanding the structure of JSON master measures objects.

Source: https://help.qlik.com/en-US/sense-developer/November2024/Subsystems/EngineAPI/Content/Sense_EngineAPI/WorkingWithAppsAndVisualizations/CreateVisualizations/create-measure.htm


## Create a master measure

A master measure is stored in the library of an app and can be used in many objects. Several generic objects can contain the same measure.

Example
The goal is to add a master measure to an app and to create a chart and a list object that use the dimension and measure that have been created.
The app, used in this example, gives information about the golf courses in some countries.


Create a master measure. The identifier of the measure is Measure01. The definition of the measure is Sum(Holes) and the label is Sum of golf course holes.

The client sends:
```json
{
  "jsonrpc": "2.0",
  "id": 3,
  "method": "CreateMeasure",
  "handle": 1,
  "params": [
    {
      "qInfo": {
        "qId": "Measure01",
        "qType": "Measure"
      },
      "qMeasure": {
        "qLabel": "Sum of golf course holes",
        "qDef": "=Sum(Holes)"
      },
      "qMetaDef": {
        "title": "Sum of golf course holes"
      }
    }
  ]
}
```

The engine returns:

```json
{
  "jsonrpc": "2.0",
  "id": 3,
  "result": {
    "qReturn": {
      "qType": "GenericMeasure",
      "qHandle": 3
    },
    "qInfo": {
      "qId": "Measure01",
      "qType": "Measure"
    }
  },
  "change": [
    3
  ]
}
```
The measure Measure01 is created and has 3 as a handle. This measure is stored in the library of the app.

CreateMeasure method.



## Use Master Measure

Create a hypercube that contains the master dimension and the master measure previously created. The hypercube uses the dimension Dimension01 that is stored in the library of the app (qLibraryId is set to Dimension01 and qFieldDefs is empty). It uses also the master measure Measure01 (qLibraryId is set to Measure01 and qDef is empty).

The client sends:

```json
{
  "jsonrpc": "2.0",
  "id": 4,
  "method": "CreateSessionObject",
  "handle": 1,
  "params": [
    {
      "qInfo": {
        "qId": "",
        "qType": "Chart"
      },
      "qHyperCubeDef": {
        "qDimensions": [
          {
            "qCalcCond": "",
            "qLibraryId": "Dimension01",
            "qDef": {
              "qFieldDefs": [],
              "qFieldLabels": [],
              "qSortCriterias": [
                {
                  "qSortByLoadOrder": 1
                }
              ],
              "qReverseSort": false
            }
          }
        ],
        "qMeasures": [
          {
            "qCalcCond": "",
            "qLibraryId": "Measure01",
            "qDef": {
              "qLabel": "Chart HC Properties measures label",
              "qDef": ""
            }
          }
        ],
        "qSuppressZero": true,
        "qSuppressMissing": true,
        "qInitialDataFetch": [
          {
            "qTop": 0,
            "qHeight": 2,
            "qLeft": 0,
            "qWidth": 2
          }
        ],
        "qCalcCond": ""
      }
    }
  ],
  "cont": false,
  "delta": false
}
```

The engine returns:

```json
{
  "jsonrpc": "2.0",
  "id": 4,
  "result": {
    "qReturn": {
      "qType": "GenericObject",
      "qHandle": 4
    }
  },
  "change": [
    4
  ]
}
```

The hypercube is created and has 4 as a handle.

HyperCubeDef.

## Create a list object. 
The list object contains the master dimension Dimension01 (qLibraryId is set to Dimension01 and qFieldDefs is empty).

The client sends:

```json
{
  "jsonrpc": "2.0",
  "id": 5,
  "method": "CreateSessionObject",
  "handle": 1,
  "params": [
    {
      "qInfo": {
        "qId": "ListObject01",
        "qType": "ListObject"
      },
      "qListObjectDef": {
        "qStateName": "$",
        "qLibraryId": "Dimension01",
        "qDef": {
          "qFieldDefs": [
            ""
          ],
          "qFieldLabels": [
            ""
          ],
          "qSortCriterias": [
            {
              "qSortByLoadOrder": 1
            }
          ],
          "FieldDefs": []
        },
        "qInitialDataFetch": [
          {
            "qTop": 0,
            "qHeight": 1,
            "qLeft": 0,
            "qWidth": 1
          }
        ]
      }
    }
  ],
  "cont": false,
  "delta": false
}
```

The engine returns:

```json
{
  "jsonrpc": "2.0",
  "id": 5,
  "result": {
    "qReturn": {
      "qType": "GenericObject",
      "qHandle": 5
    }
  },
  "change": [
    5
  ]
}
```

The list object LB01 is created and has 5 as a handle.

ListObjectDef.
