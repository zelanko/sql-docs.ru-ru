---
title: Объект Roles (TMSL) | Документация Майкрософт
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tmsl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 375a0f62bbf482a7c033d235836ea64b78cb2da2
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2018
ms.locfileid: "38983876"
---
# <a name="roles-object-tmsl"></a>Объект Roles (TMSL)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Определяет роль в модели, определяющей набор разрешений. Членство в роли состоит из принципов безопасности Windows. Можно установить фильтры для роли для ограничения доступа к конкретным объектам.  
  
## <a name="object-definition"></a>Определение объекта  
 Все объекты имеют общий набор свойств, включая имя, тип, описание, коллекцию свойств и заметки. **Роль** объекты также имеют следующие свойства.  
  
 modelPermission  
 Устанавливает область разрешений на базу данных. Допустимые значения: none,  
                  чтение,  
                  readRefresh,  
                  обновления,  
                  и администратора. См. в разделе [роли и разрешения &#40;служб Analysis Services&#41; ](../../analysis-services/multidimensional-models/roles-and-permissions-analysis-services.md) сведения о разрешениях базы данных.  
  
 члены  
 Члены состоят из имени элемента и идентификатор, где имя — псевдоним или имя участника безопасности Windows, а идентификатор — идентификатор безопасности. Оба они указываются в определение роли. См. в разделе [компоненты SID](https://msdn.microsoft.com/library/windows/desktop/aa379597\(v=vs.85\).aspx) Дополнительные сведения об идентификаторах.  
  
 разрешений таблиц  
 Разрешение таблицы является именованный объект с разрешениями, определенными с помощью выражения DAX. Это свойство является необязательным, используемая для применения фильтра безопасности.  
  
## <a name="usage"></a>Использование  
 **Роль** объекты используются в [команда Alter &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/alter-command-tmsl.md), [создать команду &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/create-command-tmsl.md), [командой createorreplace в скрипте &#40;TMSL &#41; ](../../analysis-services/tabular-models-scripting-language-commands/createorreplace-command-tmsl.md), и [команда Delete &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/delete-command-tmsl.md).  
  
 Объект **роли** объект свойства модели, но также можно указать как свойство объекта базы данных, учитывая однозначное сопоставление между моделью и базы данных.  
  
 При создании замена или изменение объекта, роли, укажите все свойства чтения и записи определения объекта. Пропуск свойства чтения и записи считается операция удаления.  
  
## <a name="full-syntax"></a>Полный синтаксис  
 Ниже приведено представление схемы роль объекта модели.  
  
```  
"roles": {  
          "type": "array",  
          "items": {  
            "description": "ModelRole object of Tabular Object Model (TOM)",  
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
              "modelPermission": {  
                "enum": [  
                  "none",  
                  "read",  
                  "readRefresh",  
                  "refresh",  
                  "administrator"  
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
              },  
              "members": {  
                "type": "array",  
                "items": {  
                  "anyOf": [  
                    {  
                      "description": "WindowsModelRoleMember object of Tabular Object Model (TOM)",  
                      "type": "object",  
                      "properties": {  
                        "memberName": {  
                          "type": "string"  
                        },  
                        "memberId": {  
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
                      "description": "ExternalModelRoleMember object of Tabular Object Model (TOM)",  
                      "type": "object",  
                      "properties": {  
                        "memberName": {  
                          "type": "string"  
                        },  
                        "memberId": {  
                          "type": "string"  
                        },  
                        "identityProvider": {  
                          "type": "string"  
                        },  
                        "memberType": {  
                          "enum": [  
                            "auto",  
                            "user",  
                            "group"  
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
                  ]  
                }  
              },  
              "tablePermissions": {  
                "type": "array",  
                "items": {  
                  "description": "TablePermission object of Tabular Object Model (TOM)",  
                  "type": "object",  
                  "properties": {  
                    "name": {  
                      "type": "string"  
                    },  
                    "filterExpression": {  
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
                }  
              }  
            },  
            "additionalProperties": false  
          }  
        }  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по языку TMSL (Tabular Model Scripting Language)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [Роли и разрешения (службы Analysis Services)](../../analysis-services/multidimensional-models/roles-and-permissions-analysis-services.md)  
  
  
