---
title: SQLXML не устанавливается в SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: 3dbb4f65-41de-48b8-ad62-47c9d7932de3
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: fb6967f2e4ca514209355901caf1a163dbf8415d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47754553"
---
# <a name="sqlxml-is-not-installed-in-sql-server"></a>SQLXML не установлен в SQL Server
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  До версии [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] компонент SQLXML 4.0 распространялся с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и входил в состав установки по умолчанию всех версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], кроме [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]. Начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], последняя версия SQLXML (SQLXML 4.0 с пакетом обновления 1 (SP1)) больше не включается в состав [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Чтобы установить SQLXML 4.0 с пакетом обновления 1, загрузите ее из [места установки для SQLXML 4.0 с пакетом обновления 1](https://www.microsoft.com/en-us/download/details.aspx?id=30403).  
  
 Если приложение выполняется в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и требует SQLXML 4.0, необходимо загрузить и установить SQLXML 4.0 с пакетом обновления 1.  
  
## <a name="sqlxml-40-sp1-behavior-with-new-data-types-using-sqloledb-and-sql-server-native-client-ole-db-provider"></a>Поведение SQLXML 4.0 при работе с новыми типами данных с помощью SQLOLEDB и поставщика OLE DB для собственного клиента SQL Server  
 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] введены следующие типы данных, которые разработчики, применяющие SQLXML может потребоваться использовать:  
  
-   **Дата**  
  
-   **Time**  
  
-   **DateTime2**  
  
-   **DateTimeOffset**  
  
 При использовании SQLXML 4.0 с пакетом обновления 1 с SQLOLEDB или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB для собственного клиента из [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], эти типы отображаются как строки для разработчика. SQLXML 4.0 SP1 позволяет использовать эти четыре новых типа данных в качестве встроенных скалярных типов при использовании с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик для собственного клиента OLE DB 11.0 или более поздней версии. Без загрузки SQLXML 4.0 с пакетом обновления 1 (SP1) при сопоставлении этих типов с нестроковыми типами может происходить усечение и потеря части данных. Например, при сопоставлении **DateTime2** для **xsd: Date** полученные данные будут усечены до [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] **DateTime** точностью 3,33 миллисекунды.  
  
## <a name="see-also"></a>См. также  
 [Основные понятия о программировании для SQLXML 4.0](../../relational-databases/sqlxml/sqlxml-4-0-programming-concepts.md)  
  
  
