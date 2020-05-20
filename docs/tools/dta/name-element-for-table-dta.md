---
title: Элемент Name описания таблицы (DTA)
description: В служебной программе DTA элемент Name описания таблицы определяет имя таблицы для настройки. В этой статье описывается этот элемент.
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Name element
ms.assetid: 422a755f-ee52-4863-b1aa-f4ef1b8fd0bb
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.openlocfilehash: cb397cf7642f4b523c0919ac70c06f6a3442ef46
ms.sourcegitcommit: b8933ce09d0e631d1183a84d2c2ad3dfd0602180
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83151858"
---
# <a name="name-element-for-table-dta"></a>Элемент Name описания таблицы (DTA)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Позволяет задать имя настраиваемой таблицы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
<Schema>  
    <Table>  
        <Name>...</Name>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|**Тип данных и длина**|**string**, от 1 до 255 символов|  
|**Значение по умолчанию**|Нет.|  
|**Наличие**|Обязательный элемент. Один раз для каждого элемента **Table** .|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент Table для схемы (DTA)](../../tools/dta/table-element-for-schema-dta.md)|  
|**Дочерние элементы**|Нет.|  
  
## <a name="example"></a>Пример  
 Пример использования см. в разделе [Элемент Server (DTA)](../../tools/dta/server-element-dta.md).  
  
## <a name="see-also"></a>См. также:  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
