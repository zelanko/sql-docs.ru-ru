---
title: Объект DataSources (TMSL) | Документация Майкрософт
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tmsl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7beabaaf63194cc699c3711a87dd1e59d244c068
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2018
ms.locfileid: "38981336"
---
# <a name="datasources-object-tmsl"></a>Объект DataSources (TMSL)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Определяет соединение с источником данных, используемым в модели, либо при импорте, чтобы добавлять данные к модели, в запросы к серверу с помощью режима DirectQuery.  Моделей в режиме DirectQuery может иметь только один **DataSource** объекта.  
  
 Если вы создаете, заменив, или изменение сам объект источника данных, любой источник данных, на которые ссылается сценарий (например, сценарий секционирования) должен быть существующим **DataSource** объекта в модели.  
  
## <a name="object-definition"></a>Определение объекта  
 Все объекты имеют общий набор свойств, включая имя, тип, описание, коллекцию свойств и заметки. **Источник данных** объекты также имеют следующие свойства.  
  
 Тип  
 Тип источника данных. В настоящее единственным допустимым значением является поставщиком (1) — обычная строка подключения.  
  
 connectionString  
 Строка подключения, как минимум указывает сервер и базу данных, но можно также включить другие свойства, поддерживаемые внешней реляционной СУБД, такие как данные поставщика или учетной записи пользователя. Это значение обязательно. См. в разделе [класс SqlConnectionStringBuilder](https://msdn.microsoft.com/library/ms254500\(v=vs.110\).aspx) подробные сведения о SQL Server базы данных свойства строки подключения.  
  
 impersonationMode  
 Указывает, следует ли служб Analysis Services олицетворяют удостоверение пользователя, запрашивающего запрос. Это свойство является числовое значение, указывающее учетные данные, используемые для олицетворения. Возможны следующие значения перечислений:  
  
-   По умолчанию (1) - сервер использует метод олицетворения, которые они подходят для контекста, в котором применяется олицетворение.  
  
-   ImpersonateAccount (2) - сервер использует указанной учетной записи.  
  
-   ImpersonateAnonymous (3) — сервер использует учетная запись анонимного пользователя.  Этот параметр не рекомендуется, но иногда используется в сценариях доступа HTTP пользовательскими приложениями, которые обрабатывают проверку подлинности.  
  
-   ImpersonateCurrentUser (4) — сервер использует учетную запись, как подключается клиент.  
  
-   ImpersonateServiceAccount (5) — сервер использует учетную запись, работает под управлением сервера.  
  
-   ImpersonateUnattendedAccount (6) — сервер использует учетную запись автоматического выполнения команд. Используется для Power Pivot или табличных моделей, которые выполняются в среде SharePoint.  
  
 Режим DirectQuery можно использовать impersonateCurrentuser, если службы Analysis Services для доверенного делегирования или  
                      impersonateServiceAccount, если запрос выполняется в контексте безопасности учетной записи службы Analysis Services. См. в разделе [Configure Analysis Services for Kerberos constrained делегирования](../../analysis-services/instances/configure-analysis-services-for-kerberos-constrained-delegation.md).  
  
 account  
 Используется для олицетворения. Учетную запись Windows или базы данных с допустимым именем входа с чтение внешней базы данных.  
  
 password  
 Зашифрованную строку, указав пароль учетной записи.  
  
 maxConnections  
 Максимальное число параллельных подключений к источнику данных.  
  
 isolation  
 Тип изоляции, который используется при выполнении команд в источнике данных. Допустимые значения: ReadCommitted (1) или моментального снимка (2).  
  
 timeout  
 Целое число, указывающее время ожидания в секундах для команд, выполняемых в источнике данных.  
  
 поставщик  
 Необязательная строка, определяющая имя управляемого поставщика данных используемого для подключения к реляционной базе данных, если не указано в строке подключения.  
  
## <a name="usage"></a>Использование  
 **Источник данных** объекты используются в [команда Alter &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/alter-command-tmsl.md), [создать команду &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/create-command-tmsl.md), [командой createorreplace в скрипте &#40; TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/createorreplace-command-tmsl.md), [команда Delete &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/delete-command-tmsl.md), [команды Refresh &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/refresh-command-tmsl.md), и [MergePartitions, команда &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/mergepartitions-command-tmsl.md).  
  
 Объект **DataSource** объект свойства модели, но также можно указать как свойство объекта базы данных, учитывая однозначное сопоставление между моделью и базы данных.  Секции, основанные на запросах SQL также указать **DataSource**, только с сокращенный набор свойств.  
  
 При создании замена или изменение объекта источника данных, укажите все свойства чтения и записи определения объекта. Пропуск свойства чтения и записи считается операция удаления.  
  
## <a name="examples"></a>Примеры  
 **Пример 1** -подключение к *FoodMart* базы данных на удаленном именованный экземпляр *Sales* на сетевом сервере с именем *Server01*.  
  
```  
"dataSources": [  
      {  
        "name": "SqlServer Server01 FoodMart",  
        "connectionString": "Provider=SQLNCLI11;Data Source=Server01\Sales;Initial Catalog=Foodmart;Integrated Security=SSPI;Persist Security Info=false",  
        "impersonationMode": "impersonateServiceAccount",  
      }  
]  
```  
  
## <a name="full-syntax"></a>Полный синтаксис  
 Ниже приведено представление схемы объекта источника данных модели.  
  
```  
"dataSources": {  
          "type": "array",  
          "items": {  
            "anyOf": [  
              {  
                "description": "ProviderDataSource object of Tabular Object Model (TOM)",  
                "type": "object",  
                "properties": {  
                  "name": {  
                    "type": "string"  
                  },  
                  "description": {  
                    "type": "string"  
                  },  
                  "type": {  
                    "enum": [  
                      "provider"  
                    ]  
                  },  
                  "connectionString": {  
                    "type": "string"  
                  },  
                  "impersonationMode": {  
                    "enum": [  
                      "default",  
                      "impersonateAccount",  
                      "impersonateAnonymous",  
                      "impersonateCurrentUser",  
                      "impersonateServiceAccount",  
                      "impersonateUnattendedAccount"  
                    ]  
                  },  
                  "account": {  
                    "type": "string"  
                  },  
                  "password": {  
                    "type": "string"  
                  },  
                  "maxConnections": {  
                    "type": "integer"  
                  },  
                  "isolation": {  
                    "enum": [  
                      "readCommitted",  
                      "snapshot"  
                    ]  
                  },  
                  "timeout": {  
                    "type": "integer"  
                  },  
                  "provider": {  
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
  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по языку TMSL (Tabular Model Scripting Language)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [Режим DirectQuery](../../analysis-services/tabular-models/directquery-mode-ssas-tabular.md)   
 [Настройка HTTP-доступа к службам Analysis Services в службах Internet Information Services (IIS) 8.0](../../analysis-services/instances/configure-http-access-to-analysis-services-on-iis-8-0.md)  
  
  
