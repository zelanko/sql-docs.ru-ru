---
title: Элемент Database описания конфигурации (DTA) | Документация Майкрософт
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
ms.assetid: e91ba243-6cc9-457a-8f5a-134f3c71ae69
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1a3547d10f325e047174f7106267b480084e88df
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48062044"
---
# <a name="database-element-for-configuration-dta"></a>Элемент Database описания конфигурации (DTA)
  Указывает базу данных, для которой нужно помощник по настройке ядра СУБД должен произвести оценку гипотетической конфигурации (определяется `Configuration` элемент).  
  
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
|**Наличие**|Требуется один или несколько раз для каждого `Server` элемент.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент Server описания конфигурации &#40;DTA&#41;](server-element-for-configuration-dta.md)|  
|**Дочерние элементы**|[Элемент Name для базы данных &#40;DTA&#41;](name-element-for-database-dta.md)<br /><br /> [Элемент schema описания базы данных &#40;DTA&#41;](schema-element-for-database-dta.md)<br /><br /> [Элемент Recommendation &#40;DTA&#41;](recommendation-element-dta.md)|  
  
## <a name="remarks"></a>Примечания  
 Этот элемент с именем **DatabaseTypecomplexType** определен в схеме XML помощника по настройке ядра СУБД. Не путайте этот элемент `Database` с элементом, родительским корневым элементом которого является элемент `Server`, находящийся в верхней части входного XML-файла. Дополнительные сведения см. в разделе [Элемент Database описания сервера (DTA)](database-element-for-server-dta.md).  
  
## <a name="example"></a>Пример  
 Пример использования этого `Database` элемент, см. в разделе [Образец входного файла XML с пользовательской конфигурацией &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>См. также  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
