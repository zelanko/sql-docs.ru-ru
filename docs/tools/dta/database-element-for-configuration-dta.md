---
title: Элемент Database для Configuration (DTA) | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Database element
ms.assetid: e91ba243-6cc9-457a-8f5a-134f3c71ae69
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 713fe8d41b4ec47e624b8fcc501c7e2b87653346
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68116936"
---
# <a name="database-element-for-configuration-dta"></a>Элемент Database описания конфигурации (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Задает базу данных, в которой помощник по настройке ядра СУБД будет оценивать гипотетическую конфигурацию (заданную элементом **Configuration** ).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
<Server>  
...code removed here...  
    <Database>...</Database>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|**Тип данных и длина**|Нет.|  
|**Значение по умолчанию**|Нет.|  
|**Наличие**|Требуется один или несколько раз для каждого элемента **Server** .|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент Server описания конфигурации (DTA)](../../tools/dta/server-element-for-configuration-dta.md)|  
|**Дочерние элементы**|[Элемент Name для базы данных (DTA)](../../tools/dta/name-element-for-database-dta.md)<br /><br /> [Элемент Schema описания базы данных (DTA)](../../tools/dta/schema-element-for-database-dta.md)<br /><br /> [Элемент Recommendation (DTA)](../../tools/dta/recommendation-element-dta.md)|  
  
## <a name="remarks"></a>Remarks  
 Этот элемент с именем **DatabaseTypecomplexType** определен в схеме XML помощника по настройке ядра СУБД. Не путайте этот элемент **Database** с элементом, родительским корневым элементом которого является элемент **Server** , находящийся в верхней части входного XML-файла. Дополнительные сведения см. в разделе [Элемент Database описания сервера (DTA)](../../tools/dta/database-element-for-server-dta.md).  
  
## <a name="example"></a>Пример  
 Пример использования элемента **Database** см. в разделе [Образец входного XML-файла с пользовательской конфигурацией (DTA)](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>См. также:  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
