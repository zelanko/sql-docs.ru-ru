---
title: MSSQLSERVER_10003 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10003 (Database Engine error)
ms.assetid: 9e2cb199-f077-4d88-8117-1b7550afc696
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e75a5e5da30ccfc7ed035693992f8a79e3b84f1b
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85781561"
---
# <a name="mssqlserver_10003"></a>MSSQLSERVER_10003
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|SQL Server|  
|Идентификатор события|10003|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|HR_E_OUTOFMEMORY|  
|Текст сообщения|Поставщик исчерпал доступный объем памяти.|  
  
## <a name="explanation"></a>Объяснение  
Из-за нехватки системной памяти поставщик OLE DB исчерпал доступный ему объем памяти.  
  
## <a name="user-action"></a>Действие пользователя  
Повторно запустите экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если это не поможет, перезапустите компьютер. Если проблема не исчезает, соберите события трассировки OLE DB с помощью приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] и передайте эти данные в службу технической поддержки поставщика OLE DB.  
  
## <a name="see-also"></a>См. также:  
[Шаблоны и разрешения приложения SQL Server Profiler](~/tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)  
[SQL Server Native Client (OLE DB)](~/relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
