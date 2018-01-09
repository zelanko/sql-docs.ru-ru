---
title: "Привязки и преобразования (OLE DB) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-date-time
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- conversions [OLE DB]
- bindings [OLE DB]
- OLE DB, bindings and conversions
ms.assetid: c187df58-a8c8-4c74-a76f-663abbc5f0c1
caps.latest.revision: "20"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 53aaa725e9d8a5079cb6a7a76d060ba4aaf64c56
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="conversions-ole-db"></a>Преобразования (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  В этом разделе описано преобразование между **datetime** и **datetimeoffset** значения. Преобразования, описанные в этом разделе, либо уже предоставлены OLE DB, либо являются согласованным расширением OLE DB.  
  
 Формат литералов и строк для дат и времени в OLE DB обычно соответствует ISO и не зависит от локали, установленной на клиенте. Единственное исключение — DBTYPE_DATE, для которого стандартом является OLE-автоматизация. Однако, поскольку собственный клиент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проводит преобразования из одного типа в другой только при передаче данных с клиента или на клиент, приложение никак не может заставить собственный клиент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проводить преобразования между типом DBTYPE_DATE и строковыми форматами. Во всех остальных случаях строки используют следующие форматы (скобками отмечены необязательные элементы).  
  
-   Формат **datetime** и **datetimeoffset** строк:  
  
     *гггг*-*мм*-*дд*[ *hh*:*мм*:*ss*[. *9999999*] [± *hh*:*мм*]]  
  
-   Формат **время** строк:  
  
     *hh*:*мм*:*ss*[. *9999999*]  
  
-   Формат **даты** строк:  
  
     *гггг*-*мм*-*дд*  
  
> [!NOTE]  
>  Предыдущие версии собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и SQLOLEDB реализовали преобразования OLE в случаях, когда стандартные преобразования возвращали ошибку. В результате некоторые преобразования, проводимые собственным клиентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] версии 10.0 и более поздних версий, отличаются от спецификации OLE DB.  
  
 Преобразования из строк обеспечивают гибкость в отношении пробелов и ширины полей. Дополнительные сведения см. в разделе «Данные форматы: строки и литералы» раздела [поддержка типов данных даты OLE DB и улучшения времени](../../relational-databases/native-client-ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md).  
  
 Далее приведены общие правила преобразования.  
  
-   При преобразовании строки в тип данных даты-времени строка сначала проходит синтаксический анализ как литерал ISO. Если анализ завершился неудачей, строка проходит синтаксический анализ как литерал даты OLE, содержащий компонент времени.  
  
-   Если время отсутствует, но получатель способен его хранить, оно устанавливается в нулевое значение. Если дата отсутствует, но принимающий объект может хранить дату, этой дате присваивается значение сегодняшней даты при использовании преобразования ISO и 30 декабря 1899 года при использовании преобразования OLE.  
  
-   Если клиент использует тип даты, в котором не указан часовой пояс, но сервер может хранить информацию о часовом поясе, предполагается, что данные клиента используют часовой пояс клиента.  
  
-   Если клиент содержит информацию о часовом поясе, но на сервере данных часового пояса нет, предполагается, что часовой пояс задан в формате UTC. Это отличается от поведения сервера.  
  
-   Если время присутствует, но получатель не способен его хранить, компонент времени пропускается.  
  
-   Если дата присутствует, но получатель не способен ее хранить, компонент даты пропускается.  
  
-   Если при преобразовании с клиента на сервер происходит усечение секунд или долей секунд, возвращается значение DB_E_ERRORSOCCURRED и устанавливается состояние DBSTATUS_E_DATAOVERFLOW.  
  
-   Если усечение секунд или долей секунд происходит при преобразовании с клиента на сервер, устанавливается состояние DBSTATUS_S_TRUNCATED.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Преобразования, выполняемые при передаче от клиента к серверу](../../relational-databases/native-client-ole-db-date-time/conversions-performed-from-client-to-server.md)  
 Описывает преобразования даты-времени, проводимые между клиентским приложением, написанным с помощью собственного клиента OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], и [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (или более поздней версией).  
  
 [Преобразования, выполняемые при передаче от сервера к клиенту](../../relational-databases/native-client-ole-db-date-time/conversions-performed-from-server-to-client.md)  
 Описывает преобразования даты-времени, проводимые между [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (или более поздней версией) и клиентским приложением, написанным с помощью собственного клиента OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также:  
 [Дата и время усовершенствования &#40; OLE DB &#41;](../../relational-databases/native-client-ole-db-date-time/date-and-time-improvements-ole-db.md)  
  
  
