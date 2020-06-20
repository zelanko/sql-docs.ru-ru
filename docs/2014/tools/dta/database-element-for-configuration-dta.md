---
title: Элемент Database для Configuration (DTA) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
ms.openlocfilehash: 045671cc386f91bb9f24caaa95cd6934fc50f5b2
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85011554"
---
# <a name="database-element-for-configuration-dta"></a>Элемент Database описания конфигурации (DTA)
  Задает базу данных, в которой помощник по настройке ядра СУБД будет оценивать гипотетическую настройку (заданную элементом `Configuration`).  
  
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
|**Наличие**|Требуется один или несколько раз для каждого элемента `Server`.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент Server описания конфигурации (DTA)](server-element-for-configuration-dta.md)|  
|**Дочерние элементы**|[Элемент Name для базы данных (DTA)](name-element-for-database-dta.md)<br /><br /> [Элемент Schema описания базы данных (DTA)](schema-element-for-database-dta.md)<br /><br /> [Элемент Recommendation (DTA)](recommendation-element-dta.md)|  
  
## <a name="remarks"></a>Remarks  
 Этот элемент с именем **DatabaseTypecomplexType** определен в схеме XML помощника по настройке ядра СУБД. Не путайте этот элемент `Database` с элементом, родительским корневым элементом которого является элемент `Server`, находящийся в верхней части входного XML-файла. Дополнительные сведения см. в разделе [Элемент Database описания сервера (DTA)](database-element-for-server-dta.md).  
  
## <a name="example"></a>Пример  
 Пример использования этого `Database` элемента см. в разделе [Образец входного XML-файла с заданной пользователем конфигурацией &#40;dta&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>См. также:  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
