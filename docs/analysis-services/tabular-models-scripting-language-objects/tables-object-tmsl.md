---
title: Объект Tables (TMSL) | Документы Microsoft
ms.custom: ''
ms.date: 05/30/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 98da08fc-8744-4d0f-bc62-e63f1e9e6b08
caps.latest.revision: 7
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 7c266fba0a8218ff7fb18c08f0b5432bef2bf15f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="tables-object-tmsl"></a>Объект Tables (TMSL)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Определяет таблиц, содержащихся в модели. Таблицы в модели либо привязаны к таблицам во внешней базе данных, из которого импортируются и запрашивать данные или вычисляемой таблицы, построенным на основе выражения DAX. В таблице один или несколько **секции** объектов описания источника данных.  Между таблицами **связь** объект указывает количество элементов, направление фильтрации и другие свойства связи.  
  
## <a name="object-definition"></a>Определение объекта  
 Все объекты имеют общий набор свойств, включая имя, тип, описание, коллекцию свойств и заметки. **Таблица** объекты также имеют следующие свойства.  
  
 dataCategory  
 Указывает тип таблицы, обычно оставляется не указан. Допустимые значения: 0 — нет, 1 - время 2 - МЕР, 3 - других, 5 - КОЛИЧЕСТВЕННЫЙ, 6-учетных ЗАПИСЕЙ, 7 - КЛИЕНТОВ, ПРОДУКТОВ-8, 9 - СЦЕНАРИЙ, 10-программы, 11 - валюты, 12 - скорости ПЕРЕДАЧИ, 13 - канал, 4 - рекламной акции, 15 - ОРГАНИЗАЦИИ, 16 - СПЕЦИФИКАЦИЯ, 17 – GEOGRAPHY.  
  
 isHidden  
 Логическое значение, указывающее, является ли таблица обрабатывается как скрытый клиентскими средствами визуализации.  
Значение true, если таблица обрабатывается как скрытая; в противном случае значение false.  
  
 столбцы  
 Представляет столбец в таблице. Это дочерний объект для объекта Table. Каждый столбец имеет несколько свойств, определенные в нем, влияющих на как клиентские приложения визуализации данных в столбце.  
  
 меры  
 Представляет значение, которое вычисляется на основе выражения. Это дочерний объект для объекта Table.  
  
 иерархии  
 Представляет коллекцию уровней, предоставляющих путь углубленной детализации логической иерархии для клиентских приложений. Это дочерний объект для объекта Table.  
  
## <a name="usage"></a>Использование  
 Список таблиц, используемых в [Alter, команда &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/alter-command-tmsl.md), [создать команду &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/create-command-tmsl.md), [команду CreateOrReplace &#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-commands/createorreplace-command-tmsl.md), [Удалить команду &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/delete-command-tmsl.md), [команда "Обновить" &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/refresh-command-tmsl.md), и [MergePartitions, команда &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/mergepartitions-command-tmsl.md).  
  
 При создании, замена или изменение объекта таблицы, укажите все свойства чтения и записи определения объекта. Пропуск свойства чтения и записи, считается удаления.  
  
## <a name="condensed-syntax"></a>Сокращенный синтаксис.  
 Определения объектов таблицы являются сложными. Этот синтаксис сворачивает внутренние свойства и объекты, чтобы дать вам подробный обзор основных частей.  
  
```  
"tables": {  
          "type": "array",  
          "items": {  
            "description": "Table object of Tabular Object Model (TOM)",  
            "type": "object",  
            "properties": {    
              "dataCategory": {  },  
              "description": {  },  
              "isHidden": {  },  
              "partitions": {  },  
              "annotations": {  },  
              "columns": {  },  
              "measures": {   },  
              "hierarchies": {  },  
```  
  
## <a name="full-syntax"></a>Полный синтаксис  
 Ниже приведено представление схемы таблиц объекта модели. Чтобы уменьшить размер этого определения, объекты раздела описаны в другом месте. В разделе [объекта секции &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/partitions-object-tmsl.md).  
  
```  
"tables": {  
          "type": "array",  
          "items": {  
            "description": "Table object of Tabular Object Model (TOM)",  
            "type": "object",  
            "properties": {  
              "name": {  
                "type": "string"  
              },  
              "dataCategory": {  
                "type": "string"  
              },  
              "description": {  
                "anyOf": [  
                  {  
                    "type": "string"  
                  },  
                  {  
                    "type": "array",  
                    "items": {  
                      "type": "string"  
                    }  
                  }  
                ]  
              },  
              "isHidden": {  
                "type": "boolean"  
              },  
              "partitions":  {   
                 },  
              "columns": {  
                "type": "array",  
                "items": {  
                  "anyOf": [  
                    {  
                      "description": "DataColumn object of Tabular Object Model (TOM)",  
                      "type": "object",  
                      "properties": {  
                        "name": {  
                          "type": "string"  
                        },  
                        "dataType": {  
                          "enum": [  
                            "automatic",  
                            "string",  
                            "int64",  
                            "double",  
                            "dateTime",  
                            "decimal",  
                            "boolean",  
                            "binary",  
                            "unknown",  
                            "variant"  
                          ]  
                        },  
                        "dataCategory": {  
                          "type": "string"  
                        },  
                        "description": {  
                          "type": "string"  
                        },  
                        "isHidden": {  
                          "type": "boolean"  
                        },  
                        "isUnique": {  
                          "type": "boolean"  
                        },  
                        "isKey": {  
                          "type": "boolean"  
                        },  
                        "isNullable": {  
                          "type": "boolean"  
                        },  
                        "alignment": {  
                          "enum": [  
                            "default",  
                            "left",  
                            "right",  
                            "center"  
                          ]  
                        },  
                        "tableDetailPosition": {  
                          "type": "integer"  
                        },  
                        "isDefaultLabel": {  
                          "type": "boolean"  
                        },  
                        "isDefaultImage": {  
                          "type": "boolean"  
                        },  
                        "summarizeBy": {  
                          "enum": [  
                            "default",  
                            "none",  
                            "sum",  
                            "min",  
                            "max",  
                            "count",  
                            "average",  
                            "distinctCount"  
                          ]  
                        },  
                        "type": {  
                          "enum": [  
                            "data",  
                            "calculated",  
                            "rowNumber",  
                            "calculatedTableColumn"  
                          ]  
                        },  
                        "formatString": {  
                          "type": "string"  
                        },  
                        "isAvailableInMdx": {  
                          "type": "boolean"  
                        },  
                        "keepUniqueRows": {  
                          "type": "boolean"  
                        },  
                        "displayOrdinal": {  
                          "type": "integer"  
                        },  
                        "sourceProviderType": {  
                          "type": "string"  
                        },  
                        "displayFolder": {  
                          "type": "string"  
                        },  
                        "sourceColumn": {  
                          "type": "string"  
                        },  
                        "sortByColumn": {  
                          "type": "string"  
                        },  
                        "annotations": {  
                          "type": "array",  
                          "items": {  
                            "description": "Annotation object of Tabular Object Model (TOM)",  
                            "type": "object",  
                            "properties": {  
                              "name": {  
                                "type": "string"  
                              },  
                              "value": {  
                                "anyOf": [  
                                  {  
                                    "type": "string"  
                                  },  
                                  {  
                                    "type": "array",  
                                    "items": {  
                                      "type": "string"  
                                    }  
                                  }  
                                ]  
                              }  
                            },  
                            "additionalProperties": false  
                          }  
                        }  
                      },  
                      "additionalProperties": false  
                    },  
                    {  
                      "description": "CalculatedTableColumn object of Tabular Object Model (TOM)",  
                      "type": "object",  
                      "properties": {  
                        "name": {  
                          "type": "string"  
                        },  
                        "dataType": {  
                          "enum": [  
                            "automatic",  
                            "string",  
                            "int64",  
                            "double",  
                            "dateTime",  
                            "decimal",  
                            "boolean",  
                            "binary",  
                            "unknown",  
                            "variant"  
                          ]  
                        },  
                        "dataCategory": {  
                          "type": "string"  
                        },  
                        "description": {  
                          "type": "string"  
                        },  
                        "isHidden": {  
                          "type": "boolean"  
                        },  
                        "isUnique": {  
                          "type": "boolean"  
                        },  
                        "isKey": {  
                          "type": "boolean"  
                        },  
                        "isNullable": {  
                          "type": "boolean"  
                        },  
                        "alignment": {  
                          "enum": [  
                            "default",  
                            "left",  
                            "right",  
                            "center"  
                          ]  
                        },  
                        "tableDetailPosition": {  
                          "type": "integer"  
                        },  
                        "isDefaultLabel": {  
                          "type": "boolean"  
                        },  
                        "isDefaultImage": {  
                          "type": "boolean"  
                        },  
                        "summarizeBy": {  
                          "enum": [  
                            "default",  
                            "none",  
                            "sum",  
                            "min",  
                            "max",  
                            "count",  
                            "average",  
                            "distinctCount"  
                          ]  
                        },  
                        "type": {  
                          "enum": [  
                            "data",  
                            "calculated",  
                            "rowNumber",  
                            "calculatedTableColumn"  
                          ]  
                        },  
                        "formatString": {  
                          "type": "string"  
                        },  
                        "isAvailableInMdx": {  
                          "type": "boolean"  
                        },  
                        "keepUniqueRows": {  
                          "type": "boolean"  
                        },  
                        "displayOrdinal": {  
                          "type": "integer"  
                        },  
                        "sourceProviderType": {  
                          "type": "string"  
                        },  
                        "displayFolder": {  
                          "type": "string"  
                        },  
                        "isNameInferred": {  
                          "type": "boolean"  
                        },  
                        "isDataTypeInferred": {  
                          "type": "boolean"  
                        },  
                        "sourceColumn": {  
                          "type": "string"  
                        },  
                        "sortByColumn": {  
                          "type": "string"  
                        },  
                        "columnOriginTable": {  
                          "type": "string"  
                        },  
                        "columnOriginColumn": {  
                          "type": "string"  
                        },  
                        "annotations": {  
                          "type": "array",  
                          "items": {  
                            "description": "Annotation object of Tabular Object Model (TOM)",  
                            "type": "object",  
                            "properties": {  
                              "name": {  
                                "type": "string"  
                              },  
                              "value": {  
                                "anyOf": [  
                                  {  
                                    "type": "string"  
                                  },  
                                  {  
                                    "type": "array",  
                                    "items": {  
                                      "type": "string"  
                                    }  
                                  }  
                                ]  
                              }  
                            },  
                            "additionalProperties": false  
                          }  
                        }  
                      },  
                      "additionalProperties": false  
                    },  
                    {  
                      "description": "CalculatedColumn object of Tabular Object Model (TOM)",  
                      "type": "object",  
                      "properties": {  
                        "name": {  
                          "type": "string"  
                        },  
                        "dataType": {  
                          "enum": [  
                            "automatic",  
                            "string",  
                            "int64",  
                            "double",  
                            "dateTime",  
                            "decimal",  
                            "boolean",  
                            "binary",  
                            "unknown",  
                            "variant"  
                          ]  
                        },  
                        "dataCategory": {  
                          "type": "string"  
                        },  
                        "description": {  
                          "type": "string"  
                        },  
                        "isHidden": {  
                          "type": "boolean"  
                        },  
                        "isUnique": {  
                          "type": "boolean"  
                        },  
                        "isKey": {  
                          "type": "boolean"  
                        },  
                        "isNullable": {  
                          "type": "boolean"  
                        },  
                        "alignment": {  
                          "enum": [  
                            "default",  
                            "left",  
                            "right",  
                            "center"  
                          ]  
                        },  
                        "tableDetailPosition": {  
                          "type": "integer"  
                        },  
                        "isDefaultLabel": {  
                          "type": "boolean"  
                        },  
                        "isDefaultImage": {  
                          "type": "boolean"  
                        },  
                        "summarizeBy": {  
                          "enum": [  
                            "default",  
                            "none",  
                            "sum",  
                            "min",  
                            "max",  
                            "count",  
                            "average",  
                            "distinctCount"  
                          ]  
                        },  
                        "type": {  
                          "enum": [  
                            "data",  
                            "calculated",  
                            "rowNumber",  
                            "calculatedTableColumn"  
                          ]  
                        },  
                        "formatString": {  
                          "type": "string"  
                        },  
                        "isAvailableInMdx": {  
                          "type": "boolean"  
                        },  
                        "keepUniqueRows": {  
                          "type": "boolean"  
                        },  
                        "displayOrdinal": {  
                          "type": "integer"  
                        },  
                        "sourceProviderType": {  
                          "type": "string"  
                        },  
                        "displayFolder": {  
                          "type": "string"  
                        },  
                        "isDataTypeInferred": {  
                          "type": "boolean"  
                        },  
                        "expression": {  
                          "type": "string"  
                        },  
                        "sortByColumn": {  
                          "type": "string"  
                        },  
                        "annotations": {  
                          "type": "array",  
                          "items": {  
                            "description": "Annotation object of Tabular Object Model (TOM)",  
                            "type": "object",  
                            "properties": {  
                              "name": {  
                                "type": "string"  
                              },  
                              "value": {  
                                "anyOf": [  
                                  {  
                                    "type": "string"  
                                  },  
                                  {  
                                    "type": "array",  
                                    "items": {  
                                      "type": "string"  
                                    }  
                                  }  
                                ]  
                              }  
                            },  
                            "additionalProperties": false  
                          }  
                        }  
                      },  
                      "additionalProperties": false  
                    }  
                  ]  
                }  
              },  
              "measures": {  
                "type": "array",  
                "items": {  
                  "description": "Measure object of Tabular Object Model (TOM)",  
                  "type": "object",  
                  "properties": {  
                    "name": {  
                      "type": "string"  
                    },  
                    "description": {  
                      "anyOf": [  
                        {  
                          "type": "string"  
                        },  
                        {  
                          "type": "array",  
                          "items": {  
                            "type": "string"  
                          }  
                        }  
                      ]  
                    },  
                    "expression": {  
                      "anyOf": [  
                        {  
                          "type": "string"  
                        },  
                        {  
                          "type": "array",  
                          "items": {  
                            "type": "string"  
                          }  
                        }  
                      ]  
                    },  
                    "formatString": {  
                      "type": "string"  
                    },  
                    "isHidden": {  
                      "type": "boolean"  
                    },  
                    "isSimpleMeasure": {  
                      "type": "boolean"  
                    },  
                    "displayFolder": {  
                      "type": "string"  
                    },  
                    "kpi": {  
                      "description": "KPI object of Tabular Object Model (TOM)",  
                      "type": "object",  
                      "properties": {  
                        "description": {  
                          "anyOf": [  
                            {  
                              "type": "string"  
                            },  
                            {  
                              "type": "array",  
                              "items": {  
                                "type": "string"  
                              }  
                            }  
                          ]  
                        },  
                        "targetDescription": {  
                          "type": "string"  
                        },  
                        "targetExpression": {  
                          "anyOf": [  
                            {  
                              "type": "string"  
                            },  
                            {  
                              "type": "array",  
                              "items": {  
                                "type": "string"  
                              }  
                            }  
                          ]  
                        },  
                        "targetFormatString": {  
                          "type": "string"  
                        },  
                        "statusGraphic": {  
                          "type": "string"  
                        },  
                        "statusDescription": {  
                          "type": "string"  
                        },  
                        "statusExpression": {  
                          "anyOf": [  
                            {  
                              "type": "string"  
                            },  
                            {  
                              "type": "array",  
                              "items": {  
                                "type": "string"  
                              }  
                            }  
                          ]  
                        },  
                        "trendGraphic": {  
                          "type": "string"  
                        },  
                        "trendDescription": {  
                          "type": "string"  
                        },  
                        "trendExpression": {  
                          "anyOf": [  
                            {  
                              "type": "string"  
                            },  
                            {  
                              "type": "array",  
                              "items": {  
                                "type": "string"  
                              }  
                            }  
                          ]  
                        },  
                        "annotations": {  
                          "type": "array",  
                          "items": {  
                            "description": "Annotation object of Tabular Object Model (TOM)",  
                            "type": "object",  
                            "properties": {  
                              "name": {  
                                "type": "string"  
                              },  
                              "value": {  
                                "anyOf": [  
                                  {  
                                    "type": "string"  
                                  },  
                                  {  
                                    "type": "array",  
                                    "items": {  
                                      "type": "string"  
                                    }  
                                  }  
                                ]  
                              }  
                            },  
                            "additionalProperties": false  
                          }  
                        }  
                      },  
                      "additionalProperties": false  
                    },  
                    "annotations": {  
                      "type": "array",  
                      "items": {  
                        "description": "Annotation object of Tabular Object Model (TOM)",  
                        "type": "object",  
                        "properties": {  
                          "name": {  
                            "type": "string"  
                          },  
                          "value": {  
                            "anyOf": [  
                              {  
                                "type": "string"  
                              },  
                              {  
                                "type": "array",  
                                "items": {  
                                  "type": "string"  
                                }  
                              }  
                            ]  
                          }  
                        },  
                        "additionalProperties": false  
                      }  
                    }  
                  },  
                  "additionalProperties": false  
                }  
              },  
              "hierarchies": {  
                "type": "array",  
                "items": {  
                  "description": "Hierarchy object of Tabular Object Model (TOM)",  
                  "type": "object",  
                  "properties": {  
                    "name": {  
                      "type": "string"  
                    },  
                    "description": {  
                      "anyOf": [  
                        {  
                          "type": "string"  
                        },  
                        {  
                          "type": "array",  
                          "items": {  
                            "type": "string"  
                          }  
                        }  
                      ]  
                    },  
                    "isHidden": {  
                      "type": "boolean"  
                    },  
                    "displayFolder": {  
                      "type": "string"  
                    },  
                    "annotations": {  
                      "type": "array",  
                      "items": {  
                        "description": "Annotation object of Tabular Object Model (TOM)",  
                        "type": "object",  
                        "properties": {  
                          "name": {  
                            "type": "string"  
                          },  
                          "value": {  
                            "anyOf": [  
                              {  
                                "type": "string"  
                              },  
                              {  
                                "type": "array",  
                                "items": {  
                                  "type": "string"  
                                }  
                              }  
                            ]  
                          }  
                        },  
                        "additionalProperties": false  
                      }  
                    },  
                    "levels": {  
                      "type": "array",  
                      "items": {  
                        "description": "Level object of Tabular Object Model (TOM)",  
                        "type": "object",  
                        "properties": {  
                          "ordinal": {  
                            "type": "integer"  
                          },  
                          "name": {  
                            "type": "string"  
                          },  
                          "description": {  
                            "anyOf": [  
                              {  
                                "type": "string"  
                              },  
                              {  
                                "type": "array",  
                                "items": {  
                                  "type": "string"  
                                }  
                              }  
                            ]  
                          },  
                          "column": {  
                            "type": "string"  
                          },  
                          "annotations": {  
                            "type": "array",  
                            "items": {  
                              "description": "Annotation object of Tabular Object Model (TOM)",  
                              "type": "object",  
                              "properties": {  
                                "name": {  
                                  "type": "string"  
                                },  
                                "value": {  
                                  "anyOf": [  
                                    {  
                                      "type": "string"  
                                    },  
                                    {  
                                      "type": "array",  
                                      "items": {  
                                        "type": "string"  
                                      }  
                                    }  
                                  ]  
                                }  
                              },  
                              "additionalProperties": false  
                            }  
                          }  
                        },  
                        "additionalProperties": false  
                      }  
                    }  
                  },  
                  "additionalProperties": false  
                }  
              }  
            },  
            "additionalProperties": false  
          }  
        }  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по языку TMSL (Tabular Model Scripting Language)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)  
  
  
