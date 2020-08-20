---
description: SQLXML не установлен в SQL Server
title: SQLXML не установлен в SQL Server
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: 3dbb4f65-41de-48b8-ad62-47c9d7932de3
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 3c0fee1b0ad59aa8a07e8f95decd94e84c6af225
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88490380"
---
# <a name="sqlxml-is-not-installed-in-sql-server"></a>SQLXML не установлен в SQL Server
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  До версии [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] компонент SQLXML 4.0 распространялся с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и входил в состав установки по умолчанию всех версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], кроме [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]. Начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], последняя версия SQLXML (SQLXML 4.0 с пакетом обновления 1 (SP1)) больше не включается в состав [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Чтобы установить SQLXML 4,0 с пакетом обновления 1 (SP1), скачайте его из [расположения установки для sqlxml 4,0 SP1](https://www.microsoft.com/download/details.aspx?id=30403).  
  
 Если приложение выполняется в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и требует sqlxml 4,0, необходимо загрузить и установить sqlxml 4,0 SP1.  
  
## <a name="sqlxml-40-sp1-behavior-with-new-data-types-using-sqloledb-and-sql-server-native-client-ole-db-provider"></a>Поведение SQLXML 4.0 при работе с новыми типами данных с помощью SQLOLEDB и поставщика OLE DB для собственного клиента SQL Server  
 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] добавлены следующие типы данных, которые могут потребоваться разработчикам, использующим SQLXML.  
  
-   **Дата**  
  
-   **Time**  
  
-   **DateTime2**  
  
-   **DateTimeOffset**  
  
 При использовании SQLXML 4,0 с пакетом обновления 1 (SP1) с поддержкой SQLOLEDB или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB из [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] эти типы отображаются как строки для разработчика. SQLXML 4,0 с пакетом обновления 1 (SP1) включит эти четыре новых типа данных в качестве встроенных скалярных типов при использовании [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента OLE DB поставщика 11,0 или более поздней версии. Без загрузки SQLXML 4.0 с пакетом обновления 1 (SP1) при сопоставлении этих типов с нестроковыми типами может происходить усечение и потеря части данных. Например, сопоставление **datetime2** с **xsd: Date** приведет к усечению данных до значения [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] **точности DateTime** , равного 3,33 миллисекундам.  
  
## <a name="see-also"></a>См. также:  
 [Основные понятия о программировании для SQLXML 4.0](../../relational-databases/sqlxml/sqlxml-4-0-programming-concepts.md)  
  
  
