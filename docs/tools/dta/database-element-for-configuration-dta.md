---
title: Элемент Database описания конфигурации (DTA) | Документация Майкрософт
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2823734aec3138dd030a0d0399d11d458a970a8a
ms.sourcegitcommit: 0f7cf9b7ab23df15624d27c129ab3a539e8b6457
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2018
ms.locfileid: "51291060"
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
  
  
