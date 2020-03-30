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
ms.openlocfilehash: 9061845efbbbf3c20b4d079af2c2b00cfeef1dfd
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "68068325"
---
# <a name="mssqlserver_10003"></a>MSSQLSERVER_10003
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
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
  
