---
title: Synchronize, команда (TMSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/13/2018
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a32ff053-f38f-49d7-afdc-e19f59c88135
caps.latest.revision: 9
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a83d10d5f8dce62837b6d86804586f5c5099e10e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="synchronize-command-tmsl"></a>Synchronize, команда (TMSL)
[!INCLUDE[ssas-appliesto-sqlas-all](../../includes/ssas-appliesto-sqlas-all.md)]

  Синхронизирует базу данных служб Analysis Services с другой базой данных.  
  
## <a name="request"></a>Запрос  
 Команда синхронизации принимаемое JSON свойства, как показано ниже.  
  
```  
{   
   "synchronize":{   
      "database":"AdventureWorksDW_Production",  
      "source":"Provider=MSOLAP.7;Data Source=localhost;Integrated Security=SSPI;Initial Catalog=AdventureWorksDW_Dev",  
      "synchronizeSecurity":"copyAll",  
      "applyCompression":true  
   }  
}  
```  
  
 Команда синхронизации принимаемое JSON свойства, как показано ниже.  
  
||||  
|-|-|-|  
|**Свойство**|**Default**|**Description**|  
|базой данных||Имя объекта базы данных для синхронизации.|  
|источник||Строка подключения, используемая для подключения к исходному серверу.|  
|synchronizeSecurity|skipMembership|Значение перечисления, определяющее способ восстановления определений безопасности, включая роли и разрешения. Допустимые значения включают skipMembership, copyAll, ignoreSecurity.|  
|applyCompression|True|Логическое значение, при значении true указывает, что сжатие будет применяться при выполнении операции синхронизации; в противном случае — значение false.|  
  
## <a name="response"></a>Ответ  
 Возвращает пустой результирующий после успешного завершения команды. В противном случае возвращается исключение XML для Аналитики.  
  
## <a name="usage-endpoints"></a>Использование (конечные точки)  
 Этот элемент команды используется в инструкции [выполнить метод &#40;XMLA&#41; ](../../analysis-services/xmla/xml-elements-methods-execute.md) вызова через конечную точку XML для Аналитики, предоставляемых одним из следующих способов:  
  
-   Как окно XMLA в SQL Server Management Studio (SSMS)  
  
-   В качестве входного файла для **invoke-ascmd** командлет PowerShell  
  
-   В качестве входных данных для задачи служб SSIS или заданием агента SQL Server  
  
 Готовый сценарий для этой команды можно создать в среде SSMS, нажав кнопку сценария, в диалоговом окне синхронизации баз данных.  
  
 [ \[MS-SSAS-T\]: Менное сервера служб Analysis Services табличной (SQL Server технические Protocol)](http://go.microsoft.com/fwlink/p/?LinkId=784855) документ содержит раздел 3.1.5.2.2, в котором описывается структура команд JSON табличных метаданных и объектов. В настоящее время этот документ охватывает команды и возможности, которые еще не реализована в сценарии TMSL. См. в разделе [языке скриптов табличных моделей &#40;TMSL&#41; ссылки](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md) для дополнительной информации о том, что поддерживается  
  
## <a name="see-also"></a>См. также  
 [Справочник по языку TMSL (Tabular Model Scripting Language)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)  
  
  
