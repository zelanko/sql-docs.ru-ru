---
title: "Создание частичных обновлений данных FILESTREAM | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-blob"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "FILESTREAM [SQL Server], FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT"
  - "FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT"
ms.assetid: d6f7661e-6c14-4d31-9541-4520ca0f82b2
caps.latest.revision: 16
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 16
---
# Создание частичных обновлений данных FILESTREAM
  Приложение использует команду FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT для выполнения частичных обновлений в данных FILESTREAM BLOB. Функция [DeviceIoControl](http://go.microsoft.com/fwlink/?LinkId=105527) передает это значение и дескриптор, возвращаемый функцией [OpenSqlFilestream](../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md) драйверу FILESTREAM. Затем драйвер принудительно реализует копирование на стороне сервера текущих данных FILESTREAM в файл, упоминаемый в дескрипторе. Если приложение выдает значение для команды FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT после того, как была произведена запись в дескриптор, то последняя операция записи будет зафиксирована, а предыдущие операции записи в дескриптор будут потеряны.  
  
> [!NOTE]  
>  Для удаленного доступа FILESTREAM использует [протокол SMB](http://go.microsoft.com/fwlink/?LinkId=112454).  
  
## Пример  
 В следующем примере показывается, как можно использовать значение команды `FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT` для выполнения частичного обновления вставленных данных FILESTREAM BLOB.  
  
> [!NOTE]  
>  Для этого примера требуется база данных с поддержкой FILESTREAM и таблица, которая создана в разделе [Создание базы данных с поддержкой FILESTREAM](../../relational-databases/blob/create-a-filestream-enabled-database.md) и [Создание таблицы для хранения данных FILESTREAM](../../relational-databases/blob/create-a-table-for-storing-filestream-data.md).  
  
 [!code-cpp[FILESTREAM#FS_CPP_FSCTL](../../relational-databases/blob/codesnippet/cpp/make-partial-updates-to-_1.cpp)]  
  
## См. также:  
 [Доступ к данным FILESTREAM с OpenSqlFilestream](../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md)   
 [Создание клиентских приложений для данных FILESTREAM](../../relational-databases/blob/create-client-applications-for-filestream-data.md)  
  
  