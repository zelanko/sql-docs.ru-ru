---
title: MSSQLSERVER_905 | Документация Майкрософт
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 905 (Database Engine error)
ms.assetid: c828bb2e-e554-4f81-b76c-2b3740d2b944
caps.latest.revision: 15
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 67003112253fc8b7b74fa4dd7c232538c9084bba
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37407103"
---
# <a name="mssqlserver905"></a>MSSQLSERVER_905
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|905|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBSTARTUP_EE_PARTITIONING|  
|Текст сообщения|Невозможно запустить базу данных "%.*ls" в этом выпуске SQL Server, так как она содержит функцию секционирования "%.\*ls". Секционирование поддерживается только в выпуске SQL Server Enterprise Edition.|  
  
## <a name="explanation"></a>Объяснение  
 База данных содержит одну или несколько секционированных таблиц или индексов. В этом выпуске [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не может использоваться секционирование. Поэтому правильный запуск базы данных невозможен. Секционированные таблицы и индексы доступны не в каждом выпуске [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Перечень функций, поддерживаемых в разных выпусках [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в разделе [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="user-action"></a>Действие пользователя  
 Отсоедините базу данных при помощи хранимой процедуры sp_detach_db. Если необходимо, переместите файлы, а затем подключите базу данных к экземпляру поддерживаемого выпуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при помощи инструкции CREATE DATABASE с параметром FOR ATTACH или FOR ATTACH_REBUILD_LOG. Отмените секционирование на всех таблицах и удалите функции секционирования. Снова отсоедините базу данных и повторно присоедините ее к текущему серверу.  
  
  
