---
title: Команда Synchronize (TMSL) | Документация Майкрософт
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tmsl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4265e6fa1e2214fae53cacdb084e152005eb3647
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38033277"
---
# <a name="synchronize-command-tmsl"></a>Команда Synchronize (TMSL)
[!INCLUDE[ssas-appliesto-sqlas-all](../../includes/ssas-appliesto-sqlas-all.md)]

  Синхронизирует базу данных служб Analysis Services с другой базой данных.  
  
## <a name="request"></a>Запрос  
 Команда synchronize принимает JSON свойства, как показано ниже.  
  
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
  
 Команда synchronize принимает JSON свойства, как показано ниже.  
  
||||  
|-|-|-|  
|**Свойство**|**Default**|**Описание**|  
|База данных||Имя объекта базы данных для синхронизации.|  
|источник||Строка подключения для подключения к исходному серверу.|  
|synchronizeSecurity|skipMembership|Значение перечисления, определяющее способ восстановления определений безопасности, включая роли и разрешения. Допустимые значения включают skipMembership, copyAll, ignoreSecurity.|  
|applyCompression|True|Логическое значение, если значение равно true, указывает, что сжатие будет применяться во время операции синхронизации; в противном случае — false.|  
  
## <a name="response"></a>Ответ  
 Возвращает пустой результат, когда команда будет выполнена. В противном случае возвращается исключение XMLA.  
  
## <a name="usage-endpoints"></a>Использование (конечные точки)  
 Этот элемент команды используется в инструкции [выполнить метод &#40;XMLA&#41; ](../../analysis-services/xmla/xml-elements-methods-execute.md) вызов через конечную точку XML для Аналитики, предоставляемых одним из следующих способов:  
  
-   Как окно XMLA в SQL Server Management Studio (SSMS)  
  
-   В качестве входного файла для **invoke-ascmd** командлет PowerShell  
  
-   В качестве входных данных задачи служб SSIS или заданием агента SQL Server  
  
 Готовый сценарий для этой команды можно создать из SSMS, щелкнув кнопку сценарий в диалоговом окне синхронизации баз данных.  
  
 [ \[MS-SSAS-T\]: QL Server табличной модели Analysis Services (SQL Server технические Protocol)](http://go.microsoft.com/fwlink/p/?LinkId=784855) документ содержит раздел 3.1.5.2.2, в котором описывается структура JSON команд табличных метаданных и объектов. В настоящее время этот документ охватывает команды и возможности, которые еще не реализована в сценарии TMSL. См. в разделе [Tabular Model Scripting Language &#40;TMSL&#41; ссылку](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md) для пояснения о том, что поддерживается  
  
## <a name="see-also"></a>См. также  
 [Справочник по языку TMSL (Tabular Model Scripting Language)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)  
  
  
