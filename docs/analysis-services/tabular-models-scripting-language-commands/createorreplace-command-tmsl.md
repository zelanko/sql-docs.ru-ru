---
title: "Команду CreateOrReplace (TMSL) | Документы Microsoft"
ms.custom: 
ms.date: 05/30/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f77a0e04-461a-4fa8-b997-78057e410d56
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: d658378bde1e3a58f36b1137328f723ad3d380d5
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="createorreplace-command-tmsl"></a>Команду CreateOrReplace (TMSL)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]Создает или заменяет указанный объект и все дочерние объекты, которые указаны. Создаются объекты не существует. Существующие объекты заменяются с новым определением.  
  
 При задании свойства чтения и записи, убедитесь, что все они входят. Пропуск чтения записи объекта считается удаления.  
  
## <a name="request"></a>Запрос  
 Структура запроса различается в зависимости от объекта. Объект, который является родительским должна включать все его дочерние элементы, несмотря на то, что полный объект определения одноуровневые элементы и родительские элементы не являются обязательными.  
  
 [Объект базы данных &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-objects/database-object-tmsl.md)  
  
 Заменяет существующую базу данных с использованием определения переименован, минимальная базы данных, которое указывает его имя, свойства измененной модели и подключение. Поскольку определение объекта не содержит таблицы, секции или связей, будут удалены все эти объекты.  
  
```  
{  
  "createOrReplace": {  
    "object": {  
      "database": "AdventureWorksTabular1200"  
    },  
    "database": {  
      "name": "TestCreateOrReplaceDB",  
      "id": "newID",  
      "compatibilityLevel": 1200,  
      "model": {  
        "defaultMode": "import",  
        "culture": "en-US",  
        "dataSources": [  
          {  
            "name": "SqlServer localhost AdventureworksDW2016",  
            "connectionString": "Provider=SQLNCLI11;Data Source=localhost;Initial Catalog=AdventureworksDW2016;Integrated Security=SSPI;Persist Security Info=false",  
            "impersonationMode": "impersonateAccount",  
            "account": "   ",  
            "annotations": [  
              {  
                "name": "ConnectionEditUISource",  
                "value": "SqlServer"  
              }  
            ]  
          }  
        ]  
      }  
    }  
  }  
}  
```  
  
 [Объект источника данных &#40; TMSL &#41; ](../../analysis-services/tabular-models-scripting-language-objects/datasources-object-tmsl.md) Заменяет имя подключения.  
  
```  
{  
  "createOrReplace": {  
    "object": {  
      "database": "TestCreateOrReplaceDB",  
      "dataSource": "SqlServer localhost AdventureworksDW2016"  
    },  
    "dataSource": {  
      "name": "New connection name",  
      "connectionString": "Provider=SQLNCLI11;Data Source=localhost;Initial Catalog=AdventureworksDW2016;Integrated Security=SSPI;Persist Security Info=false",  
      "impersonationMode": "impersonateAccount",  
      "account": "   ",  
      "annotations": [  
        {  
          "name": "ConnectionEditUISource",  
          "value": "SqlServer"  
        }  
      ]  
    }  
  }  
}  
```  
  
 [Объект Tables &#40; TMSL &#41; ](../../analysis-services/tabular-models-scripting-language-objects/tables-object-tmsl.md) Перезаписывает все существующие таблицы, оставив только от указанного.  
  
```  
{  
  "createOrReplace": {  
    "object": {  
      "database": "AdventureWorksTabular1200"  
    },  
    "database": {  
      "name": "AdventureWorksTabular1200",  
      "id": "New-AdventureWorksTabular1200",  
      "compatibilityLevel": 1200,  
      "model": {  
        "defaultMode": "import",  
        "culture": "en-US",  
        "dataSources": [  
          {  
            "name": "SqlServer localhost AdventureworksDW2016",  
            "connectionString": "Provider=SQLNCLI11;Data Source=localhost;Initial Catalog=AdventureworksDW2016;Integrated Security=SSPI;Persist Security Info=false",  
            "impersonationMode": "impersonateAccount",  
            "account": "   ",  
            "annotations": [  
              {  
                "name": "ConnectionEditUISource",  
                "value": "SqlServer"  
              }  
            ]  
          }  
        ],  
        "tables": [  
          {  
            "name": "Date",  
            "columns": [  
              {  
                "name": "DateKey",  
                "dataType": "int64",  
                "sourceColumn": "DateKey",  
                "sourceProviderType": "Integer"  
              },  
              {  
                "name": "FullDateAlternateKey",  
                "dataType": "dateTime",  
                "sourceColumn": "FullDateAlternateKey",  
                "formatString": "General Date",  
                "sourceProviderType": "DBDate"  
              },  
              {  
                "name": "CalendarYear",  
                "dataType": "int64",  
                "sourceColumn": "CalendarYear",  
                "sourceProviderType": "SmallInt"  
              }  
            ],  
            "partitions": [  
              {  
                "name": "DimDate",  
                "dataView": "full",  
                "source": {  
                  "query": " SELECT [dbo].[DimDate].* FROM [dbo].[DimDate] ",  
                  "dataSource": "SqlServer localhost AdventureworksDW2016"  
                }  
              }  
            ],  
            "annotations": [  
              {  
                "name": "_TM_ExtProp_QueryDefinition",  
                "value": " SELECT [dbo].[DimDate].* FROM [dbo].[DimDate] "  
              },  
              {  
                "name": "_TM_ExtProp_DbTableName",  
                "value": "DimDate"  
              },  
              {  
                "name": "_TM_ExtProp_DbSchemaName",  
                "value": "dbo"  
              }  
            ]  
          }  
        ]  
     }  
   }  
 }  
}   
```  
  
 [Объект секций &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-objects/partitions-object-tmsl.md)  
  
 Замените имя секции. Объекты раздела имеют три свойства чтения и записи: имя, источник, описание. При задании свойства чтения и записи, убедитесь, что все они входят. Пропуск чтения записи объекта считается удаления.  
  
 Поскольку определение объекта секции, затронутые только именованный раздел и его определение. Другие таблицы, связи и разделы не затрагиваются.  
  
 Если вы создаете, заменив, или изменение сам объект источника данных, любой источник данных, на которые ссылается сценарий (например, приведенный ниже сценарий секционирования) должен быть существующим **DataSource** объектов в модели. Если необходимо изменить источник данных, добавьте его в  
  
```  
{  
  "createOrReplace": {  
    "object": {  
      "database": "AdventureWorksTabular1200",  
      "table": "FactSalesQuota",  
      "partition": "FactSalesQuota - 2011"  
    },  
    "partition": {  
      "name": "Sales Quota for 2011",  
      "mode": "import",  
      "dataView": "full",  
      "source": {  
        "query": [  
          "SELECT [dbo].[FactSalesQuota].* FROM [dbo].[FactSalesQuota]",  
          "JOIN DimDate as DD",  
          "on DD.DateKey = FactSalesQuota.DateKey",  
          "WHERE DD.CalendarYear='2011'"  
        ],  
        "dataSource": "SqlServer localhost AdventureworksDW2016"  
      }  
    }  
  }  
}  
```  
  
 [Объект роли &#40; TMSL &#41; ](../../analysis-services/tabular-models-scripting-language-objects/roles-object-tmsl.md) Заменяет определение роли на тот, который включает в себя элементы.  
  
```  
{  
  "createOrReplace": {  
    "object": {  
      "database": "AdventureWorksTabular1200",  
      "role": "DataReader"  
    },  
    "role": {  
      "name": "DataReader",  
      "modelPermission": "read",  
      "members": [  
        {  
          "memberName": "ADVENTUREWORKS\\InternalSalesGrp"  
        }  
      ]  
    }  
  }  
}  
```  
  
## <a name="response"></a>Ответ  
 Возвращает пустой результирующий после успешного завершения команды. В противном случае возвращается исключение XML для Аналитики.  
  
## <a name="examples"></a>Примеры  
 **Пример 1** -создает новую базу данных, перезаписывая существующую базу данных с тем же именем.  
  
```  
{  
  "createOrReplace": {  
    "object": {  
      "database": "AdventureWorksTabular1200"  
    },  
    "database": {  
      "name": "AdventureWorksTabular1200",  
      "id": "AdventureWorksTabular1200",  
      "compatibilityLevel": 1200,  
      "model": {  
        "defaultMode": "directQuery",  
        "culture": "en-US",  
        "dataSources": [  
          {  
            "name": "SqlServer localhost AdventureworksDW2016",  
            "connectionString": "Provider=SQLNCLI11;Data Source=localhost;Initial Catalog=AdventureworksDW2016;Integrated Security=SSPI;Persist Security Info=false",  
            "impersonationMode": "impersonateAccount",  
            "account": "   ",  
            "annotations": [  
              {  
                "name": "ConnectionEditUISource",  
                "value": "SqlServer"  
              }  
            ]  
          }  
        ],  
        "tables": [  
          {  
            "name": "DimDate",  
            "columns": [  
              {  
                "name": "DateKey",  
                "dataType": "int64",  
                "sourceColumn": "DateKey",  
                "sourceProviderType": "Integer"  
              },  
              {  
                "name": "FullDateAlternateKey",  
                "dataType": "dateTime",  
                "sourceColumn": "FullDateAlternateKey",  
                "formatString": "General Date",  
                "sourceProviderType": "DBDate"  
              },  
              {  
                "name": "CalendarYear",  
                "dataType": "int64",  
                "sourceColumn": "CalendarYear",  
                "sourceProviderType": "SmallInt"  
              }  
            ],  
            "partitions": [  
              {  
                "name": "DimDate",  
                "dataView": "full",  
                "source": {  
                  "query": " SELECT [dbo].[DimDate].* FROM [dbo].[DimDate] ",  
                  "dataSource": "SqlServer localhost AdventureworksDW2016"  
                }  
              }  
            ],  
            "annotations": [  
              {  
                "name": "_TM_ExtProp_QueryDefinition",  
                "value": " SELECT [dbo].[DimDate].* FROM [dbo].[DimDate] "  
              },  
              {  
                "name": "_TM_ExtProp_DbTableName",  
                "value": "DimDate"  
              },  
              {  
                "name": "_TM_ExtProp_DbSchemaName",  
                "value": "dbo"  
              }  
            ]  
          },  
          {  
            "name": "DimEmployee",  
            "columns": [  
              {  
                "name": "EmployeeKey",  
                "dataType": "int64",  
                "sourceColumn": "EmployeeKey",  
                "sourceProviderType": "Integer"  
              },  
              {  
                "name": "SalesTerritoryKey",  
                "dataType": "int64",  
                "sourceColumn": "SalesTerritoryKey",  
                "sourceProviderType": "Integer"  
              },  
              {  
                "name": "FirstName",  
                "dataType": "string",  
                "sourceColumn": "FirstName",  
                "sourceProviderType": "WChar"  
              },  
              {  
                "name": "LastName",  
                "dataType": "string",  
                "sourceColumn": "LastName",  
                "sourceProviderType": "WChar"  
              },  
              {  
                "name": "MiddleName",  
                "dataType": "string",  
                "sourceColumn": "MiddleName",  
                "sourceProviderType": "WChar"  
              },  
              {  
                "name": "SalesPersonFlag",  
                "dataType": "boolean",  
                "sourceColumn": "SalesPersonFlag",  
                "formatString": "\"TRUE\";\"TRUE\";\"FALSE\"",  
                "sourceProviderType": "Boolean"  
              },  
              {  
                "name": "DepartmentName",  
                "dataType": "string",  
                "sourceColumn": "DepartmentName",  
                "sourceProviderType": "WChar"  
              }  
            ],  
            "partitions": [  
              {  
                "name": "DimEmployee",  
                "dataView": "full",  
                "source": {  
                  "query": " SELECT [dbo].[DimEmployee].* FROM [dbo].[DimEmployee] ",  
                  "dataSource": "SqlServer localhost AdventureworksDW2016"  
                }  
              }  
            ],  
            "annotations": [  
              {  
                "name": "_TM_ExtProp_QueryDefinition",  
                "value": " SELECT [dbo].[DimEmployee].* FROM [dbo].[DimEmployee] "  
              },  
              {  
                "name": "_TM_ExtProp_DbTableName",  
                "value": "DimEmployee"  
              },  
              {  
                "name": "_TM_ExtProp_DbSchemaName",  
                "value": "dbo"  
              }  
            ]  
          },  
          {  
            "name": "FactSalesQuota",  
            "columns": [  
              {  
                "name": "SalesQuotaKey",  
                "dataType": "int64",  
                "sourceColumn": "SalesQuotaKey",  
                "sourceProviderType": "Integer"  
              },  
              {  
                "name": "EmployeeKey",  
                "dataType": "int64",  
                "sourceColumn": "EmployeeKey",  
                "sourceProviderType": "Integer"  
              },  
              {  
                "name": "DateKey",  
                "dataType": "int64",  
                "sourceColumn": "DateKey",  
                "sourceProviderType": "Integer"  
              },  
              {  
                "name": "CalendarYear",  
                "dataType": "int64",  
                "sourceColumn": "CalendarYear",  
                "sourceProviderType": "SmallInt"  
              },  
              {  
                "name": "SalesAmountQuota",  
                "dataType": "decimal",  
                "sourceColumn": "SalesAmountQuota",  
                "formatString": "\\$#,0.00;(\\$#,0.00);\\$#,0.00",  
                "sourceProviderType": "Currency",  
                "annotations": [  
                  {  
                    "name": "Format",  
                    "value": "\<Format Format=\"Currency\" Accuracy=\"2\" ThousandSeparator=\"True\">\<Currency LCID=\"1033\" DisplayName=\"$ English (United States)\" Symbol=\"$\" PositivePattern=\"0\" NegativePattern=\"0\" /></Format>"  
                  }  
                ]  
              },  
              {  
                "name": "Date",  
                "dataType": "dateTime",  
                "sourceColumn": "Date",  
                "formatString": "General Date",  
                "sourceProviderType": "DBTimeStamp"  
              }  
            ],  
            "partitions": [  
              {  
                "name": "FactSalesQuota",  
                "dataView": "full",  
                "source": {  
                  "query": " SELECT [dbo].[FactSalesQuota].* FROM [dbo].[FactSalesQuota] ",  
                  "dataSource": "SqlServer localhost AdventureworksDW2016"  
                }  
              },  
              {  
                "name": "FactSalesQuota - 2011",  
                "mode": "import",  
                "dataView": "sample",  
                "source": {  
                  "query": [  
                    "SELECT [dbo].[FactSalesQuota].* FROM [dbo].[FactSalesQuota]",  
                    "JOIN DimDate as DD",  
                    "on DD.DateKey = FactSalesQuota.DateKey",  
                    "WHERE DD.CalendarYear='2011'"  
                  ],  
                  "dataSource": "SqlServer localhost AdventureworksDW2016"  
                },  
                "annotations": [  
                  {  
                    "name": "QueryEditorSerialization",  
                    "value": [  
                      "\<?xml version=\"1.0\" encoding=\"UTF-16\"?>\<Gemini xmlns=\"QueryEditorSerialization\"><AnnotationContent><![CDATA[<RSQueryCommandText>SELECT [dbo].[FactSalesQuota].* FROM [dbo].[FactSalesQuota]",  
                      "JOIN DimDate as DD",  
                      "on DD.DateKey = FactSalesQuota.DateKey",  
                      "WHERE DD.CalendarYear='2011'</RSQueryCommandText><RSQueryCommandType>Text</RSQueryCommandType><RSQueryDesignState></RSQueryDesignState>]]></AnnotationContent></Gemini>"  
                    ]  
                  }  
                ]  
              }  
            ],  
            "annotations": [  
              {  
                "name": "_TM_ExtProp_QueryDefinition",  
                "value": " SELECT [dbo].[FactSalesQuota].* FROM [dbo].[FactSalesQuota] "  
              },  
              {  
                "name": "_TM_ExtProp_DbTableName",  
                "value": "FactSalesQuota"  
              },  
              {  
                "name": "_TM_ExtProp_DbSchemaName",  
                "value": "dbo"  
              }  
            ]  
          }  
        ],  
        "relationships": [  
          {  
            "name": "4426b078-193f-4a59-bc52-33f990bfb7da",  
            "fromTable": "FactSalesQuota",  
            "fromColumn": "DateKey",  
            "toTable": "DimDate",  
            "toColumn": "DateKey"  
          },  
          {  
            "name": "cde1e139-4553-4d0a-a025-1cd98e35aab2",  
            "fromTable": "FactSalesQuota",  
            "fromColumn": "EmployeeKey",  
            "toTable": "DimEmployee",  
            "toColumn": "EmployeeKey"  
          }  
        ]  
      }  
    }  
  }  
}  
  
```  
  
## <a name="usage-endpoints"></a>Использование (конечные точки)  
 Этот элемент команды используется в инструкции [выполнить метод &#40; XML для Аналитики &#41; ](../../analysis-services/xmla/xml-elements-methods-execute.md) вызова через конечную точку XML для Аналитики, предоставляемых одним из следующих способов:  
  
-   Как окно XMLA в SQL Server Management Studio (SSMS)  
  
-   В качестве входного файла для **invoke-ascmd** командлет PowerShell  
  
-   В качестве входных данных для задачи служб SSIS или заданием агента SQL Server  
  
 Готовый сценарий для этой команды можно создать в среде SSMS.  Например, можно щелкнуть правой кнопкой мыши существующую базу данных > **сценарий** > **скрипта базы данных в качестве** > **СОЗДАНИЯ или ЗАМЕНЫ для**.  
  
 [ \[MS-SSAS-T\]: Менное сервера служб Analysis Services табличной (SQL Server технические Protocol)](http://go.microsoft.com/fwlink/p/?LinkId=784855) документ содержит раздел 3.1.5.2.2, в котором описывается структура команд JSON табличных метаданных и объектов. В настоящее время этот документ охватывает команды и возможности, которые еще не реализована в сценарии TMSL. См. в разделе [языке скриптов табличных моделей &#40; TMSL &#41; Справочник по](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md) для дополнительной информации о том, что поддерживается  

## <a name="see-also"></a>См. также:  
 [Справочник по языку TMSL (Tabular Model Scripting Language)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)  
  
  
