---
title: SQLXML не устанавливается в SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: 3dbb4f65-41de-48b8-ad62-47c9d7932de3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 7561d2d22439112ea084f1f8a62c32aeb5591cfc
ms.sourcegitcommit: aa4f594ec6d3e85d0a1da6e69fa0c2070d42e1d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59240762"
---
# <a name="sqlxml-is-not-installed-in-sql-server"></a>SQLXML не установлен в SQL Server
  До версии [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] компонент SQLXML 4.0 распространялся с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и входил в состав установки по умолчанию всех версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], кроме [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]. Начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], последняя версия SQLXML (SQLXML 4.0 с пакетом обновления 1 (SP1)) больше не включается в состав [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Чтобы установить SQLXML 4.0 с пакетом обновления 1, если это возможно, загрузите ее из [места установки для SQLXML с пакетом обновления 1](https://www.microsoft.com/download/details.aspx?id=16978).  
  
 Если приложение выполняется в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и требует SQLXML 4.0, а на компьютере не установлен [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], необходимо загрузить и установить SQLXML 4.0 с пакетом обновления 1 (SP1).  
  
## <a name="sqlxml-40-sp1-behavior-with-new-data-types-using-sqloledb-and-sql-server-native-client-ole-db-provider"></a>Поведение SQLXML 4.0 при работе с новыми типами данных с помощью SQLOLEDB и поставщика OLE DB для собственного клиента SQL Server  
 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] предоставляет следующие типы данных, которые разработчики, применяющие SQLXML может потребоваться использовать:  
  
-   `Date`  
  
-   `Time`  
  
-   `DateTime2`  
  
-   `DateTimeOffset`  
  
 При использовании SQLXML 4.0 с пакетом обновления 1 (SP1) совместно с SQLOLEDB (из компонентов Windows DAC, ранее известных как компоненты MDAC) или совместно с поставщиком [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB для собственного клиента [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] эти новые типы будут доступны разработчику в виде строк. SQLXML 4.0 с пакетом обновления 1 (SP1) позволяет использовать эти четыре новых типа данных в качестве встроенных скалярных типов в поставщике OLE DB версии 11.0 для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Без загрузки SQLXML 4.0 с пакетом обновления 1 (SP1) при сопоставлении этих типов с нестроковыми типами может происходить усечение и потеря части данных. Например, при сопоставлении `DateTime2` для `xsd:date` полученные данные будут усечены до [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] `DateTime` точностью 3,33 миллисекунды.  
  
## <a name="see-also"></a>См. также  
 [Основные понятия о программировании для SQLXML 4.0](sqlxml-4-0-programming-concepts.md)  
  
  
