---
title: "MSSQLSERVER_905 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 905 (Database Engine error)
ms.assetid: c828bb2e-e554-4f81-b76c-2b3740d2b944
caps.latest.revision: "14"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 648f373a5e1054ae72a462914072391f5560dce0
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
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
  
