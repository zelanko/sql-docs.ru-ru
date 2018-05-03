---
title: Файл элемента (DTA) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: dta
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- XML
helpviewer_keywords:
- File element
ms.assetid: 73dce835-9a80-4aef-8e0f-9dcf07dd5b80
caps.latest.revision: 15
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e04127c12690c89a0a6a98c116fe90381237795c
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MTE
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="file-element-dta"></a>Элемент File (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Служит для указания файла рабочей нагрузки. Рабочая нагрузка представляет собой набор инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] , выполняемый в одной или нескольких базах данных, которые необходимо настроить. Файлы рабочей нагрузки могут представлять собой скрипты [!INCLUDE[tsql](../../includes/tsql-md.md)] (SQL) или файлы трассировки (TRC). Дополнительные сведения см. в разделе[Start and Use the Database Engine Tuning Advisor](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
<DTAInput>  
  <Server>...</Server>  
  <Workload>  
    <File>...</File>  
  </Workload>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Description|  
|--------------------|-----------------|  
|**Тип данных и длина**|Для задания пути к каталогу, в котором находится файл рабочей загрузки, используется тип данных **string** . Пример:<br /><br /> `<File>C:\Tuning\tun.sql</File>`<br /><br /> Помните, что ограничение на длину устанавливается сервером.|  
|**Значение по умолчанию**|Нет.|  
|**Наличие**|Необходимо наличие одного такого элемента, если не задан никакой другой тип рабочей нагрузки. Для родительского элемента **Workload**необходимо задать дочерний элемент **EventString**, **File** или **Database** , однако одновременно может использоваться только один из них. Например, если рабочая нагрузка задана элементом **File** , то в том же входном XML-файле уже нельзя задать рабочую нагрузку элементом **Database** .|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент Workload (DTA)](../../tools/dta/workload-element-dta.md)|  
|**Дочерние элементы**|Нет.|  
  
## <a name="example"></a>Пример  
 Пример использования этого элемента см. в разделе [Образец простого входного файла XML (DTA)](../../tools/dta/simple-xml-input-file-sample-dta.md).  
  
## <a name="see-also"></a>См. также:  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
