---
title: Объект связи (TMSL) | Документы Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6ff65f5781145d1716cc232d9d73e1521541a24c
ms.sourcegitcommit: 1aedef909f91dc88dc741748f36eabce3a04b2b1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/08/2018
---
# <a name="relationships-object-tmsl"></a>Объект связи (TMSL)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Определяет связь между исходной и целевой таблицы, с возможностью указать количество элементов и направление фильтры запросов и безопасности.  
  
## <a name="object-definition"></a>Определение объекта  
 Все объекты имеют общий набор свойств, включая имя, тип, описание, коллекцию свойств и заметки. **Связь** объекты также имеют следующие свойства.  
  
 isActive  
 Логическое значение, указывающее, помечена ли связь как активным или неактивным. Активная связь автоматически используется для фильтрации в таблицах. Неактивная связь может использоваться явным образом в вычислениях DAX с применением функции USERELATIONSHIP.  
  
 crossFilteringBehavior  
 Указывает, как связи влияют на фильтрацию данных. В разделе [двунаправленные кросс-фильтры для табличных моделей в SQL Server 2016 Analysis Services](../../analysis-services/tabular-models/bi-directional-cross-filters-tabular-models-analysis-services.md) для получения дополнительной информации. Допустимы следующие значения:  
  
-   Значением OneDirection (1) — строк, выбранных в поле «Кому» конце связи автоматически профильтрует результаты сканирования таблицы в «От» конце связи.  
  
-   BothDirections (2) - фильтры на каждом конце связи автоматически профильтруют другой таблицы.  
  
-   Автоматический (3) - обработчик анализа связей и выберите один из вариантов поведения с помощью эвристики.  
  
 joinOnDateBehavior  
 При объединении двух столбцов даты и времени указывает, идет ли объединение по дате и времени или только по дате.  
  
-   Присоединиться к DateAndTime (1) — при объединении двух столбцов, в дате и времени.  
  
-   (2) при объединении двух столбцов, DatePartOnly соединения только по дате.  
  
 relyOnReferentialIntegrity  
 Не используется — зарезервировано для будущего использования.  
  
 отношениями securityFilteringBehavior  
 Перечисление, указывающее, как связи влияют на фильтрацию данных при вычислении выражения безопасности уровня строк. Допустимы следующие значения:  
  
-   Значением OneDirection (1) — строк, выбранных в поле «Кому» конце связи автоматически профильтрует результаты сканирования таблицы в «От» конце связи.  
  
-   BothDirections (2) - фильтры на каждом конце связи автоматически профильтруют другой таблицы.  
  
## <a name="usage"></a>Использование  
 Связи объектов используются в [Alter, команда &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/alter-command-tmsl.md), [создать команду &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/create-command-tmsl.md), [команду CreateOrReplace &#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-commands/createorreplace-command-tmsl.md), и [удалить команду &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/delete-command-tmsl.md).  
  
 При создании, замена или изменение связи объекта, укажите все свойства чтения и записи определения объекта. Пропуск свойства чтения и записи, считается удаления.  
  
## <a name="full-syntax"></a>Полный синтаксис  
 Ниже приведено представление схемы объекта связи.  
  
```  
"relationships": {  
          "type": "array",  
          "items": {  
            "anyOf": [  
              {  
                "description": "SingleColumnRelationship object of Tabular Object Model (TOM)",  
                "type": "object",  
                "properties": {  
                  "name": {  
                    "type": "string"  
                  },  
                  "isActive": {  
                    "type": "boolean"  
                  },  
                  "type": {  
                    "enum": [  
                      "singleColumn"  
                    ]  
                  },  
                  "crossFilteringBehavior": {  
                    "enum": [  
                      "oneDirection",  
                      "bothDirections",  
                      "automatic"  
                    ]  
                  },  
                  "joinOnDateBehavior": {  
                    "enum": [  
                      "dateAndTime",  
                      "datePartOnly"  
                    ]  
                  },  
                  "relyOnReferentialIntegrity": {  
                    "type": "boolean"  
                  },  
                  "securityFilteringBehavior": {  
                    "enum": [  
                      "oneDirection",  
                      "bothDirections"  
                    ]  
                  },  
                  "fromCardinality": {  
                    "enum": [  
                      "none",  
                      "one",  
                      "many"  
                    ]  
                  },  
                  "toCardinality": {  
                    "enum": [  
                      "none",  
                      "one",  
                      "many"  
                    ]  
                  },  
                  "fromColumn": {  
                    "type": "string"  
                  },  
                  "fromTable": {  
                    "type": "string"  
                  },  
                  "toColumn": {  
                    "type": "string"  
                  },  
                  "toTable": {  
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
        }  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по языку TMSL (Tabular Model Scripting Language)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [Создание связей](../../integration-services/data-flow/transformations/create-relationships.md)  
  
  
