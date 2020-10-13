---
title: Частичное обновление данных FILESTREAM | Документация Майкрософт
description: Узнайте, как использовать значение FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT для частичного обновления данных BLOB-объекта FILESTREAM. Просмотрите пример частичного обновления.
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT
- FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT
ms.assetid: d6f7661e-6c14-4d31-9541-4520ca0f82b2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3b47cdacd079bfa1235427938b3fa214a1babeb7
ms.sourcegitcommit: 04cf7905fa32e0a9a44575a6f9641d9a2e5ac0f8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/07/2020
ms.locfileid: "91809908"
---
# <a name="make-partial-updates-to-filestream-data"></a>Создание частичных обновлений данных FILESTREAM
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Приложение использует команду FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT для выполнения частичных обновлений в данных FILESTREAM BLOB. Функция [DeviceIoControl](/windows/win32/api/ioapiset/nf-ioapiset-deviceiocontrol) передает это значение и дескриптор, возвращаемый функцией [OpenSqlFilestream](../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md) драйверу FILESTREAM. Затем драйвер принудительно реализует копирование на стороне сервера текущих данных FILESTREAM в файл, упоминаемый в дескрипторе. Если приложение выдает значение для команды FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT после того, как была произведена запись в дескриптор, то последняя операция записи будет зафиксирована, а предыдущие операции записи в дескриптор будут потеряны.  
  
> [!NOTE]  
>  Для удаленного доступа FILESTREAM использует [протокол SMB](/windows/win32/fileio/microsoft-smb-protocol-and-cifs-protocol-overview) .  
  
## <a name="example"></a>Пример  
 В следующем примере показывается, как можно использовать значение команды `FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT` для выполнения частичного обновления вставленных данных FILESTREAM BLOB.  
  
> [!NOTE]  
>  Для этого примера требуется база данных с поддержкой FILESTREAM и таблица, которая создана в разделе [Создание базы данных с поддержкой FILESTREAM](../../relational-databases/blob/create-a-filestream-enabled-database.md) и [Создание таблицы для хранения данных FILESTREAM](../../relational-databases/blob/create-a-table-for-storing-filestream-data.md).  
  
 [!code-cpp[FILESTREAM#FS_CPP_FSCTL](../../relational-databases/blob/codesnippet/cpp/make-partial-updates-to-_1.cpp)]  
  
## <a name="see-also"></a>См. также:  
 [Доступ к данным FILESTREAM с OpenSqlFilestream](../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md)   
 [Создание клиентских приложений для данных FILESTREAM](../../relational-databases/blob/create-client-applications-for-filestream-data.md)  
  
