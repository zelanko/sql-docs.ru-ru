---
title: Данные большого двоичного объекта (SQL Server) | Документация Майкрософт
description: С помощью FILESTREAM, таблиц FileTable и удаленного хранилища больших двоичных объектов (RBS) SQL Server может хранить большие двоичные объекты в базе данных или в удаленном хранилище. Сравнение вариантов хранения больших двоичных объектов.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], design and implementation
ms.assetid: 97509274-c3f8-43e5-a37c-52f1ffe0961a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 15673e9ee67b4499a3c20729a73eb063610baedc
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85781740"
---
# <a name="binary-large-object-blob-data-sql-server"></a>Данные большого двоичного объекта (SQL Server)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имеет решения для хранения файлов и документов в базе данных или на удаленных устройствах хранения.  
  
## <a name="compare-options-for-storing-blobs-in-sql-server"></a>Сравнение вариантов хранения больших двоичных объектов в SQL Server

Сравнение преимуществ FILESTREAM, таблиц FileTable и удаленного хранилища больших двоичных объектов. См статью [Сравнение вариантов хранения больших двоичных объектов &#40;SQL Server&#41;](../../relational-databases/blob/compare-options-for-storing-blobs-sql-server.md).
  
##  <a name="options-for-storing-blobs"></a>Варианты хранения больших двоичных объектов  

### <a name="filestream-40sql-server41"></a>[FILESTREAM (SQL Server)](../../relational-databases/blob/filestream-sql-server.md)  

FILESTREAM позволяет приложениям на основе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]хранить в файловой системе неструктурированные данные, например документы и изображения. Приложения могут одновременно использовать многопоточные API-интерфейсы и производительность файловой системы, тем самым обеспечивая транзакционную согласованность между неструктурированными и соответствующими им структурированными данными.  
  
### <a name="filetables-40sql-server41"></a>[FileTables (SQL Server)](../../relational-databases/blob/filetables-sql-server.md)  

Функция FileTable обеспечивает поддержку пространства имен файлов Windows и совместимость с приложениями Windows для файлов данных, хранящихся в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Таблица FileTable позволяет приложению интегрировать свои компоненты хранения и управления данными, а также обеспечивает работу интегрированных служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , включая полнотекстовый и семантический поиск, с неструктурированными данными и метаданными.  
  
 Иными словами, появляется возможность хранить файлы и документы в специальных таблицах на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , называемых таблицами FileTable, но при этом доступ к ним возможен из приложений Windows без внесения каких-либо изменений в эти приложения, как если бы они хранились в файловой системе.  
  
### <a name="remote-blob-store-40rbs41-40sql-server41"></a>[Удаленное хранилище больших двоичных объектов (RBS) (SQL Server)](../../relational-databases/blob/remote-blob-store-rbs-sql-server.md)  

Удаленное хранилище больших двоичных объектов для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] позволяет администраторам баз данных сохранять большие двоичные объекты в отдельных хранилищах вместо хранения прямо на сервере. При этом значительно экономится место на диске и дорогостоящие аппаратные ресурсы сервера. Для удаленного хранилища больших двоичных объектов имеется набор API-библиотек, определяющих стандартизированную модель для приложений, осуществляющих доступ к данным BLOB. Кроме того, в RBS реализованы средства обслуживания, например сборка мусора, что позволяет более эффективно управлять удаленными данными больших двоичных объектов.  
  
 Хранилище RBS включено в установочный носитель [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , но не устанавливается программой установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
  
