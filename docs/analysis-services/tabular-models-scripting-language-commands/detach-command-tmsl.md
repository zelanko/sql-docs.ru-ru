---
title: Detach, команда (TMSL) | Документы Microsoft
ms.custom: ''
ms.date: 05/30/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 413b49cb-ea8f-415c-a059-ce692b7771a1
caps.latest.revision: 8
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 14035c9b257a494b072fe5314a9329f216b4e3b9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="detach-command-tmsl"></a>Detach, команда (TMSL)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Отсоединяет базу данных служб Analysis Services на сервере.  
  
## <a name="request"></a>Запрос  
  
```  
{   
   "detach": {    
      "database":"AdventureWorksDW2014",  
      "password": "secret"  
   }  
}  
```  
  
 Свойства, принимаемое JSON detach, команда, как показано ниже.  
  
||||  
|-|-|-|  
|**Свойство**|**Default**|**Description**|  
|базой данных|[Обязательно]|Имя объекта базы данных для отсоединения.|  
|password|Пустой|Пароль, используемый для шифрования секретов в отсоединенной базы данных.|  
  
## <a name="response"></a>Ответ  
 Возвращает пустой результирующий после успешного завершения команды. В противном случае возвращается исключение XML для Аналитики.  
  
## <a name="usage-endpoints"></a>Использование (конечные точки)  
 Этот элемент команды используется в инструкции [выполнить метод &#40;XMLA&#41; ](../../analysis-services/xmla/xml-elements-methods-execute.md) вызова через конечную точку XML для Аналитики, предоставляемых одним из следующих способов:  
  
-   Как окно XMLA в SQL Server Management Studio (SSMS)  
  
-   В качестве входного файла для **invoke-ascmd** командлет PowerShell  
  
-   В качестве входных данных для задачи служб SSIS или заданием агента SQL Server  
  
 Готовый сценарий для этой команды можно создать в среде SSMS, щелкнув кнопку сценарий в диалоговом окне отсоединения.  
  
 [ \[MS-SSAS-T\]: Менное сервера служб Analysis Services табличной (SQL Server технические Protocol)](http://go.microsoft.com/fwlink/p/?LinkId=784855) документ содержит раздел 3.1.5.2.2, в котором описывается структура команд JSON табличных метаданных и объектов. В настоящее время этот документ охватывает команды и возможности, которые еще не реализована в сценарии TMSL. См. в разделе ([языке скриптов табличных моделей &#40;TMSL&#41; ссылки](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)) для дополнительной информации о том, что поддерживается.  

## <a name="see-also"></a>См. также  
 [Справочник по языку TMSL (Tabular Model Scripting Language)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [Присоединение и отсоединение баз данных служб Analysis Services](../../analysis-services/multidimensional-models/attach-and-detach-analysis-services-databases.md)  
  
  
