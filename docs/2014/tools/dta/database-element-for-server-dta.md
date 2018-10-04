---
title: Элемент Database описания сервера (DTA) | Документация Майкрософт
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
- Database element
ms.assetid: 5cd9a87a-af4b-45f3-8c18-f7fd7e7d3064
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 341c267b686a56a37390e0ee774df0aa20e73fd8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48049824"
---
# <a name="database-element-for-server-dta"></a>Элемент Database описания сервера (DTA)
  Позволяет задать базу данных, которую необходимо настроить на конкретном сервере.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
<Server>  
...code removed here...  
    <Database>...</Database>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Нет.|  
|Значение по умолчанию|Нет.|  
|Наличие|Требуется один или несколько раз для каждого `Server` элемент.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|Родительский элемент|[Элемент Server &#40;DTA&#41;](server-element-dta.md)|  
|Дочерние элементы|[Элемент Name для базы данных &#40;DTA&#41;](name-element-for-database-dta.md)<br /><br /> [Элемент schema описания базы данных &#40;DTA&#41;](schema-element-for-database-dta.md)|  
  
## <a name="remarks"></a>Примечания  
 Этот элемент с именем **DatabaseDetailsTypecomplexType** определен в схеме XML помощника по настройке ядра СУБД. Не путайте этот элемент `Database` с элементом, корневым родительским элементом которого является `Configuration`. Дополнительные сведения см. в разделе [Элемент Database для конфигурации (DTA)](database-element-for-configuration-dta.md).  
  
## <a name="example"></a>Пример  
 Пример использования `Database` элемент, см. в разделе [элемент Server &#40;DTA&#41;](server-element-dta.md).  
  
## <a name="see-also"></a>См. также  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
