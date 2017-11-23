---
title: "RESTORE, команда (TMSL) | Документы Microsoft"
ms.custom: 
ms.date: 05/30/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 360a1567-67ae-459d-8865-9a2bef8d4186
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 85ea749ca2cd2b4fdcbcbc0ec2e07f01820e377f
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="restore-command-tmsl"></a>RESTORE, команда (TMSL)

[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

  Восстанавливает базу данных служб Analysis Services из файла резервной копии.  
  
## <a name="request"></a>Запрос  
  
```  
    {  
"restore": {  
            "description": "Parameters of Restore command of Analysis Services JSON API",  
            "properties": {  
            "database": {  
                "type": "string"  
            },  
            "file": {  
                "type": "string"  
            },  
            "password": {  
                "type": "string"  
            },  
            "dbStorageLocation": {  
                "type": "string"  
            },  
            "allowOverwrite": {  
                "type":boolean  
            },  
            "readWriteMode": {  
                "enum": [  
                "readWrite",  
                "readOnly",  
                "readOnlyExclusive"  
                ]  
. . .   
```  
  
 **Восстановление** имеет несколько свойств.  
  
||||  
|-|-|-|  
|**Свойство**|**Default**|**Description**|  
|базой данных|[Обязательно]|Имя объекта базы данных для восстановления.|  
|файл|[Обязательно]|Имя и путь к файлу резервной копии.|  
|password|Пустой|Пароль, используемый для расшифровки файла резервной копии.|  
|allowOverwrite|False|Логическое значение, если значение равно true, указывает, где уже существует файл резервной копии будет перезаписан. в противном случае — значение false.|  
|readWriteMode|ReadWrite|Значение перечисления, указывающее режимы доступа, может быть базы данных.<br /><br /> **Ниже приведены значения перечисления.**<br /><br /> readWrite – разрешен доступ для чтения и записи.<br /><br /> только для чтения — разрешен доступ только для чтения.<br /><br /> readOnlyExclusive — только для чтения монопольный доступ.|  
|dbStorageLocation|Пустой|Место хранения для восстановленной базы данных.|  
  
## <a name="response"></a>Ответ  
 Возвращает пустой результирующий после успешного завершения команды. В противном случае возвращается исключение XML для Аналитики.  
  
## <a name="example"></a>Пример  
 **Пример 1** -восстановление базы данных из локальной папки.  
  
```  
{   
   "restore": {   
      "database":"AdventureWorksDW2014",  
      "file":"c:\\awdbdwfile.abf",  
      "security":"...",  
      "allowOverwrite":"true",  
      "password":"..",  
      "locations":"d:\\SQL Server Analysis Services\\data\\",  
      "storageLocation":".."  
   }  
}  
```  
  
## <a name="usage-endpoints"></a>Использование (конечные точки)  
 Этот элемент команды используется в инструкции [выполнить метод &#40; XML для Аналитики &#41; ](../../analysis-services/xmla/xml-elements-methods-execute.md) вызова через конечную точку XML для Аналитики, предоставляемых одним из следующих способов:  
  
-   Как окно XMLA в SQL Server Management Studio (SSMS)  
  
-   В качестве входного файла для **invoke-ascmd** командлет PowerShell  
  
-   В качестве входных данных для задачи служб SSIS или заданием агента SQL Server  
  
 Готовый сценарий для этой команды можно создать в среде SSMS, нажав кнопку сценария, в диалоговом окне Восстановление.  
  
 [ \[MS-SSAS-T\]: Менное сервера служб Analysis Services табличной (SQL Server технические Protocol)](http://go.microsoft.com/fwlink/p/?LinkId=784855) документ содержит раздел 3.1.5.2.2, в котором описывается структура команд JSON табличных метаданных и объектов. В настоящее время этот документ охватывает команды и возможности, которые еще не реализована в сценарии TMSL. См. в разделе [языке скриптов табличных моделей &#40; TMSL &#41; Справочник по](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md) для дополнительной информации о том, что поддерживается  
  
## <a name="see-also"></a>См. также:  
 [Справочник по языку TMSL (Tabular Model Scripting Language)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [Создание и восстановление резервных копий баз данных служб Analysis Services](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
  
