---
title: Элемент Server (DTA) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Server element
ms.assetid: 9fe0bfb4-3aa6-4eb2-a83e-c0d0e7d4e9f6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 27385486005645f73cd488893c50be12ae2e704b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48066541"
---
# <a name="server-element-dta"></a>Элемент Server (DTA)
  Содержит сведения идентификации сервера, на котором находятся настраиваемые базы данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
<DTAInput>  
    <Server>  
    ...code removed here...  
    </Server>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|**Тип данных и длина**|Нет.|  
|**Значение по умолчанию**|Нет.|  
|**Наличие**|Требуется один раз на `DTAInput` элемент.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент DTAInput &#40;DTA&#41;](dtainput-element-dta.md)|  
|**Дочерние элементы**|[Элемент Name для Server &#40;DTA&#41;](name-element-for-server-dta.md)<br /><br /> [Элемент Database описания сервера &#40;DTA&#41;](database-element-for-server-dta.md)|  
  
## <a name="remarks"></a>Примечания  
 Можно указать только один `Server` элемент для `DTAInput` элемент. Этот элемент с именем **ServerDetailsTypecomplexType** определен в схеме XML DTA. Не путайте этот `Server` с элементом, который является дочерним объектом `Configuration` элемент. Дополнительные сведения см. в разделе [Элемент Server описания конфигурации (DTA)](server-element-for-configuration-dta.md).  
  
## <a name="example"></a>Пример  
 Следующий пример иллюстрирует, как указать таблицу **Sales.SalesPerson** в базе данных **AdventureWorks** на сервере SERVER001:  
  
```xml  
<Server>  
  <Name>SERVER001</Name>  
  <Database>  
    <Name>AdventureWorks</Name>  
    <Schema>  
      <Name>Sales</Name>  
      <Table>  
        <Name>SalesPerson</Name>  
      </Table>  
    </Schema>  
  </Database>  
</Server  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
