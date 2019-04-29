---
title: Настройка компонента Database Engine — Filestream | Документация Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], about FILESTREAM
ms.assetid: 641a10a1-ae52-4d26-8f1c-a032a4aeff02
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 190a6ce588ed40ab7cc9181476ca3730eeef34b5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63035654"
---
# <a name="database-engine-configuration---filestream"></a>Настройка компонента Database Engine — Filestream
  Эта страница используется, чтобы включить FILESTREAM для этой установки [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Хранилище FILESTREAM объединяет [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] с помощью NTFS файловая система, сохраняя `varbinary(max)` данные больших двоичных объектов (BLOB) в файловой системе в виде файлов. [!INCLUDE[tsql](../../includes/tsql-md.md)] можно вставлять, обновлять, запрашивать, искать и создавать резервные копии данных FILESTREAM. Интерфейсы файловой системы Win32 предоставляют потоковый доступ к этим данным.  
  
## <a name="uielement-list"></a>Список элементов пользовательского интерфейса  
 **Разрешить FILESTREAM при доступе через Transact-SQL**  
 Выберите, чтобы включить FILESTREAM для доступа [!INCLUDE[tsql](../../includes/tsql-md.md)] . Необходимо выбрать этот элемент управления, прежде чем будут доступны другие параметры управления.  
  
 **Разрешить FILESTREAM при потоковом доступе файлового ввода-вывода**  
 Выберите, чтобы разрешить потоковый доступ Win32 для FILESTREAM.  
  
 **Имя общего ресурса Windows**  
 Этот элемент управления используется для ввода имени общего ресурса Windows, в котором будут храниться данные FILESTREAM.  
  
 **Разрешить удаленным клиентам потоковый доступ к данным FILESTREAM**  
 Выберите этот элемент управления, чтобы разрешить удаленным клиентам доступ к этим данным FILESTREAM на этом сервере.  
  
## <a name="see-also"></a>См. также:  
 [Включение и настройка FILESTREAM](../../relational-databases/blob/enable-and-configure-filestream.md)   
 [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
