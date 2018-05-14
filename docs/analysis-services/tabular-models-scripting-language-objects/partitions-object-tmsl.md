---
title: Объект секции (TMSL) | Документы Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tmsl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5ef6371ab2dca177aa02fa04883017c4c90d2c0b
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="partitions-object-tmsl"></a>Объект секции (TMSL)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Определяет секции или логическая сегментация набора строк таблицы. Раздел состоит из SQL-запрос, используется для импорта данных для образца данных в среде моделирования или в виде запроса данных полный доступ через выполнения запросов через DirectQuery.  
  
 Свойства секции определяют источники данных для таблицы.  В иерархии объекта родительского объекта секции является объектом таблицы.  
  
## <a name="object-definition"></a>Определение объекта  
 Все объекты имеют общий набор свойств, включая имя, тип, описание, коллекцию свойств и заметки. **Раздел** объекты также имеют следующие свойства.  
  
 Тип  
 Тип раздела. Допустимые значения являются числовыми и укажите следующие данные:  
  
-   Запрос (1) — данные в этой секции извлекается, выполнив запрос к **DataSource**. **DataSource** должен быть источником данных, определенных в файле model.bim.  
  
-   Вычисляемый (2) — данные в этой секции заполняются с вычисляемое выражение.  
  
-   Нет (3) – данные в этой секции заполняется, включая набор строк данных на сервере как часть операции обновления.  
  
 mode  
 Определяет режим запроса секции. Допустимые значения: **импорта**, **DirectQuery**, или **по умолчанию** (наследуется). Это значение обязательно.  
  
|||  
|-|-|  
|**Импорт**|Указывает запрос, который запросы создаются к подсистема аналитики в памяти, хранение импортированных данных.|  
|**DirectQuery**|Проходят через выполнения запроса внешней реляционной базой данных. Режим DirectQuery использует секций для предоставления данных образца, используемых во время разработки модели. При развертывании на рабочем сервере, необходимо переключиться обратно в представление полного набора данных. Помните, что режим DirectQuery требует один раздел на таблицы и один источник данных на модель.|  
|**default**|Установите, чтобы переключить выше вверх по дереву объектов на уровне модели или базы данных. Если выбрано по умолчанию, режим запроса будет import или DirectQuery.|  
  
 источник  
 Определяет местоположение данных запроса. Допустимые значения: **запросов, вычисляемых**, или **нет**. Это значение обязательно.  
  
|||  
|-|-|  
|**Нет**|Используется для режим импорта, где данные загружаются и хранятся в памяти.|  
|**Запрос**|Для режима DirectQuery, это SQL-запрос, выполняемый для реляционной базы данных, указанной в модели **DataSource**. В разделе [объектов источников данных &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/datasources-object-tmsl.md).|  
|**Вычисляемый**|Вычисляемые таблицы получают данные из выражения, указанного при создании таблицы. Это выражение считается Источник секции, созданные для вычисляемой таблицы.|  
  
 DataView  
 Для секций DirectQuery является свойством дополнительных dataView указывает ли запрос, получающий данные образец или полного набора данных. Допустимые значения: **полного**, **пример**, или **по умолчанию** (наследуется). Как уже отмечалось, образцы используются только во время моделирования и тестирования данных. В разделе [Добавление демонстрационных данных в модель DirectQuery в режиме конструктора](../../analysis-services/tabular-models/add-sample-data-to-a-directquery-model-in-design-mode.md) для получения дополнительной информации.  
  
## <a name="usage"></a>Использование  
 Объекты секции используются в [Alter, команда &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/alter-command-tmsl.md), [создать команду &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/create-command-tmsl.md), [команду CreateOrReplace &#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-commands/createorreplace-command-tmsl.md), [Удалить команду &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/delete-command-tmsl.md), [команда "Обновить" &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/refresh-command-tmsl.md), и [MergePartitions, команда &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/mergepartitions-command-tmsl.md).  
  
 При создании, замена или изменение объект partition укажите все свойства чтения и записи определения объекта. Пропуск свойства чтения и записи, считается удаления. Свойства чтения и записи включают имя, описание, режим и источник.  
  
## <a name="examples"></a>Примеры  
 **Пример 1** -структуру простой разделов таблицы (а не таблицей фактов).  
  
```  
"partitions": [  
          {  
            "name": "Customer",  
            "source": {  
              "query": "SELECT [dbo].[Customer].* FROM [dbo].[Customer]",  
              "dataSource": "SqlServer localhost FoodmartDB"  
            }  
]  
```  
  
 **Пример 2** - секционированных данных фактов обычно основаны на предложения WHERE, которое создает неперекрывающиеся секции для данных из одной таблицы.  
  
```  
"partitions": [  
          {  
            "name": "sales_fact_2015",  
            "source": {  
              "query": "SELECT [dbo].[sales_fact_2015].* FROM [dbo].[sales_fact_2015] WHERE [dbo].[sales_fact_2015].[Quarter]=4",                                                                                          
              "dataSource": "SqlServer localhost FoodmartDB"  
            },  
          }  
        ]  
```  
  
 **Пример 3** -вычисляемой таблицы на основании выражения DAX.  
  
```  
"partitions": [  
          {  
            "name": "CalcTable1",  
            "source": {  
              "type": "calculated",  
              "expression": "'Product Class'"  
            },  
            }  
]  
```  
  
## <a name="full-syntax"></a>Полный синтаксис  
 Ниже приведено представление схемы объекта секции.  
  
```  
"partitions": {  
                "type": "array",  
                "items": {  
                  "description": "Partition object of Tabular Object Model (TOM)",  
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
                    "mode": {  
                      "enum": [  
                        "import",  
                        "directQuery",  
                        "default"  
                      ]  
                    },  
                    "dataView": {  
                      "enum": [  
                        "full",  
                        "sample",  
                        "default"  
                      ]  
                    },  
                    "source": {  
                      "anyOf": [  
                        {  
                          "description": "QueryPartitionSource object of Tabular Object Model (TOM)",  
                          "type": "object",  
                          "properties": {  
                            "type": {  
                              "enum": [  
                                "query",  
                                "calculated",  
                                "none"  
                              ]  
                            },  
                            "query": {  
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
                            "dataSource": {  
                              "type": "string"  
                            }  
                          },  
                          "additionalProperties": false  
                        },  
                        {  
                          "description": "CalculatedPartitionSource object of Tabular Object Model (TOM)",  
                          "type": "object",  
                          "properties": {  
                            "type": {  
                              "enum": [  
                                "query",  
                                "calculated",  
                                "none"  
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
                            }  
                          },  
                          "additionalProperties": false  
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
                }  
              },  
  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по языку TMSL (Tabular Model Scripting Language)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)  
  
  
