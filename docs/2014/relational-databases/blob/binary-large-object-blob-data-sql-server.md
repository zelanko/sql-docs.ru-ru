---
title: Данные большого двоичного объекта (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], design and implementation
ms.assetid: 97509274-c3f8-43e5-a37c-52f1ffe0961a
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 7f549f1c851ff09b165dae055b8bb18f01a66fcb
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66010341"
---
# <a name="binary-large-object-blob-data-sql-server"></a>Данные большого двоичного объекта (SQL Server)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имеет решения для хранения файлов и документов в базе данных или на удаленных устройствах хранения.  
  
##  <a name="in-this-section"></a><a name="section"></a>В этом разделе  
 [Сравнение параметров для хранения больших двоичных объектов (SQL Server)](compare-options-for-storing-blobs-sql-server.md)  
 Сравнение преимуществ FILESTREAM, таблиц FileTable и удаленного хранилища больших двоичных объектов.  
  
 [FILESTREAM (SQL Server)](filestream-sql-server.md)  
 FILESTREAM позволяет приложениям на основе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]хранить в файловой системе неструктурированные данные, например документы и изображения. Приложения могут одновременно использовать многопоточные API-интерфейсы и производительность файловой системы, тем самым обеспечивая транзакционную согласованность между неструктурированными и соответствующими им структурированными данными.  
  
 [FileTables (SQL Server)](filetables-sql-server.md)  
 Функция FileTable обеспечивает поддержку пространства имен файлов Windows и совместимость с приложениями Windows для файлов данных, хранящихся в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Таблица FileTable позволяет приложению интегрировать свои компоненты хранения и управления данными, а также обеспечивает работу интегрированных служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , включая полнотекстовый и семантический поиск, с неструктурированными данными и метаданными.  
  
 Иными словами, появляется возможность хранить файлы и документы в специальных таблицах на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , называемых таблицами FileTable, но при этом доступ к ним возможен из приложений Windows без внесения каких-либо изменений в эти приложения, как если бы они хранились в файловой системе.  
  
 [Удаленное хранилище больших двоичных объектов (RBS) (SQL Server)](remote-blob-store-rbs-sql-server.md)  
 Удаленное хранилище больших двоичных объектов для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] позволяет администраторам баз данных сохранять большие двоичные объекты в отдельных хранилищах вместо хранения прямо на сервере. При этом значительно экономится место на диске и дорогостоящие аппаратные ресурсы сервера. Для удаленного хранилища больших двоичных объектов имеется набор API-библиотек, определяющих стандартизированную модель для приложений, осуществляющих доступ к данным BLOB. Кроме того, в RBS реализованы средства обслуживания, например сборка мусора, что позволяет более эффективно управлять удаленными данными больших двоичных объектов.  
  
 Хранилище RBS включено в установочный носитель [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , но не устанавливается программой установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
  
