---
title: MSSQLSERVER_905 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 905 (Database Engine error)
ms.assetid: c828bb2e-e554-4f81-b76c-2b3740d2b944
caps.latest.revision: 14
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 76429f207f2b233827c77ed983025852a85adf77
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2018
ms.locfileid: "34325995"
---
# <a name="mssqlserver905"></a>MSSQLSERVER_905
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
База данных содержит одну или несколько секционированных таблиц или индексов. В этом выпуске [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не может использоваться секционирование. Поэтому правильный запуск базы данных невозможен. Секционированные таблицы и индексы доступны не в каждом выпуске [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Сведения о функциях, поддерживаемых различными выпусками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в статье [Возможности, поддерживаемые выпусками SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
## <a name="user-action"></a>Действие пользователя  
Отсоедините базу данных при помощи хранимой процедуры sp_detach_db. Если необходимо, переместите файлы, а затем подключите базу данных к экземпляру поддерживаемого выпуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при помощи инструкции CREATE DATABASE с параметром FOR ATTACH или FOR ATTACH_REBUILD_LOG. Отмените секционирование на всех таблицах и удалите функции секционирования. Снова отсоедините базу данных и повторно присоедините ее к текущему серверу.  
  
