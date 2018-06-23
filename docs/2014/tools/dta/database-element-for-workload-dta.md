---
title: Элемент Database описания рабочей нагрузки (DTA) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- XML
helpviewer_keywords:
- Database element
ms.assetid: 112fca2a-37e5-4162-b2e7-b56eb8ab0c6f
caps.latest.revision: 12
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 6380708319286a984ef54ef3820fab22821047bf
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36097830"
---
# <a name="database-element-for-workload-dta"></a>Элемент Database описания рабочей нагрузки (DTA)
  Указывает базу данных, в которой находится таблица трассировки рабочей нагрузки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
<Workload>  
  <Database>  
   ...code removed here...  
  </Database>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|**Тип данных и длина**|Нет.|  
|**Значение по умолчанию**|Нет.|  
|**Наличие**|Необходимо наличие одного такого элемента, если не задан никакой другой тип рабочей нагрузки. Необходимо указать `EventString`, `File`, или `Database` дочерний элемент `Workload` можно использовать родительский, но только один тип. Например, если рабочая нагрузка определена посредством элемента `Database`, в том же входном XML-файле нельзя указывать рабочую нагрузку также с помощью элемента `File`.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент Workload &#40;DTA&#41;](workload-element-dta.md)|  
|**Дочерние элементы**|[Элемент Name для базы данных &#40;DTA&#41;](name-element-for-database-dta.md)<br /><br /> [Элемент schema описания базы данных &#40;DTA&#41;](schema-element-for-database-dta.md)|  
  
## <a name="remarks"></a>Примечания  
 Этот элемент с именем **DatabaseDetailsTypecomplexType** определен в схеме XML помощника по настройке ядра СУБД. Не путайте этот элемент `Database` с элементом, корневым родительским элементом которого является `Configuration`. (См. раздел [Элемент Database описания конфигурации (DTA)](database-element-for-configuration-dta.md).)  
  
## <a name="example"></a>Пример  
 Пример использования этого `Database` элемента, см. пример кода в [элемент Workload &#40;DTA&#41;](workload-element-dta.md).  
  
## <a name="see-also"></a>См. также  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  