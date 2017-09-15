---
title: "Вопросы безопасности XML | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML security in ADO
ms.assetid: fadbd38e-6e7b-4b81-96ea-85169c664374
caps.latest.revision: 3
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: fc94f80cde09f6ad55de3a108b6fd16ef74444f1
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="xml-security-considerations"></a>Вопросы безопасности XML
Сохраните ADO и открытых методов в объекте набора записей не считаются безопасные операции для запуска в Internet Explorer. Таким образом Если эти методы используются в коде скрипта, который выполняется в приложение или элемент управления, размещенные в браузере, параметры безопасности браузера будет оказывать влияние на его поведение.  
  
 Internet Explorer 5 обеспечивает ограничения безопасности для таких операций, по умолчанию в зоне Интернета. В этой конфигурации не может упростить любой доступ к локальной файловой системы на клиентском компьютере или получить доступ к источникам данных за пределами домена сервера, из которого было загружено страницы набора записей. В частности при выполнении в рамках узла обозревателя, набор записей можно сохранить обратно в файл только в том случае, если она находится на том же сервере, откуда было загрузить страницу. Аналогичным образом можно открыть набор записей, загрузив его из файла только в том случае, если этот файл находится на том же сервере, откуда было загрузить страницу.  
  
## <a name="see-also"></a>См. также:  
 [Сохранение записей в формате XML](../../../ado/guide/data/persisting-records-in-xml-format.md)
