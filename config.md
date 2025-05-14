```
{
  "metadata": {
    "tenantId": "mz"
  },
  "fields": {
    "person": {
      "name": {
        "firstName": {
          "type": "string",
          "source": {
            "header": "First Name"
          }
        },
        "lastName": {
          "type": "string",
          "source": {
            "header": "Last Name"
          }
        }
      },
      "age": {
        "type": "number",
        "source": {
          "header": "Age"
        }
      },
      "hobbies": {
        "type": "array",
        "source": {
          "header": "Hobbies",
          "delimiter": ","
        },
        "items": {
          "type": "object",
          "properties": {
            "hobby": {
              "type": "string",
              "valueFrom": "self"
            },
            "addedBy": {
              "type": "string",
              "valueFrom": "$person.name.firstName"
            },
            "tenantId": {
              "type": "string",
              "value": "mz"
            },
            "roles": {
              "type": "array",
              "source": {
                "header": "Roles",
                "delimiter": ","
              },
              "items": {
                "type": "object",
                "properties": {
                  "role": {
                    "type": "string",
                    "valueFrom": "self"
                  },
                  "tenantId": {
                    "type": "string",
                    "value": "mz"
                  }
                }
              }
            }
          }
        }
      }
    },
    "status": {
      "isActive": {
        "type": "boolean",
        "source": {
          "header": "Is Active"
        },
        "transform": {
          "trueIfIn": ["a", "b", "c"]
        }
      }
    },
    "sumTarget": {
      "type": "number",
      "transform": {
        "sumOf": ["target1", "target2", "target3"]
      }
    },
    "fullConsolidatedDate": {
      "type": "string",
      "transform": {
        "combinationOf": ["day", "month", "year"],
        "delimiter": "/"
      }
    }
  }
}
```
