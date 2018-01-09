---
title: "SQLXML не установлен в SQL Server | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 3dbb4f65-41de-48b8-ad62-47c9d7932de3
caps.latest.revision: "17"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f45c7bfd04d974f661756fb06cacda3d34cb808d
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="sqlxml-is-not-installed-in-sql-server"></a>SQLXML не установлен в SQL Server
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]Прежде чем [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], SQLXML 4.0 распространялся с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и входил в состав установки по умолчанию для всех [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] версии, за исключением [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]. Начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], последняя версия SQLXML (SQLXML 4.0 с пакетом обновления 1 (SP1)) больше не включается в состав [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Чтобы установить SQLXML 4.0 с пакетом обновления 1, загрузите его из [места установки для SQLXML 4.0 с пакетом обновления 1](https://www.microsoft.com/en-us/download/details.aspx?id=30403).  
  
 Если приложение выполняется в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и требует SQLXML 4.0, необходимо загрузить и установить SQLXML 4.0 с пакетом обновления 1.  
  
## <a name="sqlxml-40-sp1-behavior-with-new-data-types-using-sqloledb-and-sql-server-native-client-ole-db-provider"></a>Поведение SQLXML 4.0 при работе с новыми типами данных с помощью SQLOLEDB и поставщика OLE DB для собственного клиента SQL Server  
 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]появились следующие типы данных, может потребоваться использовать какие разработчики, применяющие SQLXML:  
  
-   **Дата**  
  
-   **Time**  
  
-   **DateTime2**  
  
-   **DateTimeOffset**  
  
 При использовании SQLXML 4.0 с пакетом обновления 1 с SQLOLEDB или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB для собственного клиента из [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], эти типы отображаются как строки для разработчика. SQLXML 4.0 с пакетом обновления 1 позволяет использовать эти четыре новых типа данных в качестве встроенных скалярных типов при использовании с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик собственного клиента OLE DB 11.0 или более поздней версии. Без загрузки SQLXML 4.0 с пакетом обновления 1 (SP1) при сопоставлении этих типов с нестроковыми типами может происходить усечение и потеря части данных. Например, при сопоставлении **DateTime2** для **xsd: Date** данные будут усечены до [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] **DateTime** точностью до 3,33 миллисекунды.  
  
## <a name="see-also"></a>См. также:  
 [Основные понятия о программировании для SQLXML 4.0](../../relational-databases/sqlxml/sqlxml-4-0-programming-concepts.md)  
  
  
