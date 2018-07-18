---
title: Частичное обновление данных FILESTREAM | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.suite: sql
ms.technology: filestream
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT
- FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT
ms.assetid: d6f7661e-6c14-4d31-9541-4520ca0f82b2
caps.latest.revision: 16
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 23bd3b82da83b466a137eaba15da2e1998df4ca3
ms.sourcegitcommit: abd71294ebc39695d403e341c4f77829cb4166a8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2018
ms.locfileid: "36833812"
---
# <a name="make-partial-updates-to-filestream-data"></a>Создание частичных обновлений данных FILESTREAM
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Приложение использует команду FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT для выполнения частичных обновлений в данных FILESTREAM BLOB. Функция [DeviceIoControl](http://go.microsoft.com/fwlink/?LinkId=105527) передает это значение и дескриптор, возвращаемый функцией [OpenSqlFilestream](../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md) драйверу FILESTREAM. Затем драйвер принудительно реализует копирование на стороне сервера текущих данных FILESTREAM в файл, упоминаемый в дескрипторе. Если приложение выдает значение для команды FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT после того, как была произведена запись в дескриптор, то последняя операция записи будет зафиксирована, а предыдущие операции записи в дескриптор будут потеряны.  
  
> [!NOTE]  
>  Для удаленного доступа FILESTREAM использует [протокол SMB](http://go.microsoft.com/fwlink/?LinkId=112454) .  
  
## <a name="example"></a>Пример  
 В следующем примере показывается, как можно использовать значение команды `FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT` для выполнения частичного обновления вставленных данных FILESTREAM BLOB.  
  
> [!NOTE]  
>  Для этого примера требуется база данных с поддержкой FILESTREAM и таблица, которая создана в разделе [Создание базы данных с поддержкой FILESTREAM](../../relational-databases/blob/create-a-filestream-enabled-database.md) и [Создание таблицы для хранения данных FILESTREAM](../../relational-databases/blob/create-a-table-for-storing-filestream-data.md).  
  
 [!code-cpp[FILESTREAM#FS_CPP_FSCTL](../../relational-databases/blob/codesnippet/cpp/make-partial-updates-to-_1.cpp)]  
  
## <a name="see-also"></a>См. также:  
 [Доступ к данным FILESTREAM с OpenSqlFilestream](../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md)   
 [Создание клиентских приложений для данных FILESTREAM](../../relational-databases/blob/create-client-applications-for-filestream-data.md)  
  
  
