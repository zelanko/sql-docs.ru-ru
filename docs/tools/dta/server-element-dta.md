---
title: Элемент Server (DTA)
description: В служебной программе dta элемент Server содержит сведения для идентификации сервера, на котором размещены настраиваемые базы данных.
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Server element
ms.assetid: 9fe0bfb4-3aa6-4eb2-a83e-c0d0e7d4e9f6
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.openlocfilehash: 38fbe7a5027f6abd2c753b37f8419602577fc145
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85732075"
---
# <a name="server-element-dta"></a>Элемент Server (DTA)

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

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
|**Наличие**|Требуется один раз на каждый элемент **DTAInput** .|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент DTAInput (DTA)](../../tools/dta/dtainput-element-dta.md)|  
|**Дочерние элементы**|[Элемент Name описания сервера (DTA)](../../tools/dta/name-element-for-server-dta.md)<br /><br /> [Элемент Database описания сервера (DTA)](../../tools/dta/database-element-for-server-dta.md)|  
  
## <a name="remarks"></a>Remarks  
 Вы можете указать только один элемент **Server** для элемента **DTAInput** . Этот элемент с именем **ServerDetailsTypecomplexType** определен в схеме XML DTA. Не следует путать данный элемент **Server** с дочерним элементом элемента **Configuration** . Дополнительные сведения см. в разделе [Элемент Server описания конфигурации (DTA)](../../tools/dta/server-element-for-configuration-dta.md).  
  
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
  
## <a name="see-also"></a>См. также:  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
