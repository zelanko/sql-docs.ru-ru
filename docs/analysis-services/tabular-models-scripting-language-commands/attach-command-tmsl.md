---
title: "Attach, команда (TMSL) | Документы Microsoft"
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
ms.assetid: 7a12d148-eac9-4e6c-a222-1439e0817c64
caps.latest.revision: "10"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 995e77345c2770f59db620afb1ced2085eaeefa2
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="attach-command-tmsl"></a>Attach, команда (TMSL)

[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

  Присоединяет файл служб Analysis Services на сервере.  
  
  
## <a name="request"></a>Запрос  
  
```  
{   
   "attach":{   
      "folder":"C:\\Program Files\\Microsoft SQL Server\\MSAS13.Tabular\\OLAP\\Data\\",  
      "readWriteMode":"readOnly",  
      "password":"secret"  
   }  
}  
```  
  
 Команда присоединения свойства, принимаемое JSON, как показано ниже.  
  
||||  
|-|-|-|  
|**Свойство**|**Default**|**Description**|  
|базой данных|[Обязательно]|Имя объекта базы данных для присоединения.|  
|folder|[Обязательно]|Папка, содержащая присоединенной базе данных.|  
|password|Пустой|Пароль, используемый для шифрования секретных данных в присоединенной базе данных.|  
|readWriteMode|ReadWrite|Значение перечисления, указывающее режимы доступа, может быть базы данных.<br /><br /> **Ниже приведены значения перечисления.**<br /><br /> readWrite – разрешен доступ для чтения и записи.<br /><br /> только для чтения — разрешен доступ только для чтения.<br /><br /> readOnlyExclusive — только для чтения монопольный доступ.|  
  
## <a name="response"></a>Ответ  
 Возвращает пустой результирующий после успешного завершения команды. В противном случае возвращается исключение XML для Аналитики.  
  
## <a name="usage-endpoints"></a>Использование (конечные точки)  
 Этот элемент команды используется в инструкции [выполнить метод &#40; XML для Аналитики &#41; ](../../analysis-services/xmla/xml-elements-methods-execute.md) вызова через конечную точку XML для Аналитики, предоставляемых одним из следующих способов:  
  
-   Как окно XMLA в SQL Server Management Studio (SSMS)  
  
-   В качестве входного файла для **invoke-ascmd** командлет PowerShell  
  
-   В качестве входных данных для задачи служб SSIS или заданием агента SQL Server  
  
 Готовый сценарий для этой команды можно создать в среде SSMS, щелкнув кнопку сценарий в диалоговом окне Присоединение базы данных.  
  
 [ \[MS-SSAS-T\]: Менное сервера служб Analysis Services табличной (SQL Server технические Protocol)](http://go.microsoft.com/fwlink/p/?LinkId=784855) документ содержит раздел 3.1.5.2.2, в котором описывается структура команд JSON табличных метаданных и объектов. В настоящее время этот документ охватывает команды и возможности, которые еще не реализована в сценарии TMSL. См. в разделе [языке скриптов табличных моделей &#40; TMSL &#41; Справочник по](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md) для дополнительной информации о том, что поддерживается  

## <a name="see-also"></a>См. также:  
 [Справочник по языку TMSL (Tabular Model Scripting Language)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [Подключение и отключение баз данных служб Analysis Services](../../analysis-services/multidimensional-models/attach-and-detach-analysis-services-databases.md)  
  
  
