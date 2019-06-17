---
title: MSSQLSERVER_10001 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10001 (Database Engine error)
ms.assetid: f8fd2d8d-a4af-4b6a-ba51-9123b7e4c9bf
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 022b1ca3c1ab4c0e1921cbac86c3059f10087f21
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62916365"
---
# <a name="mssqlserver10001"></a>MSSQLSERVER_10001
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|10001|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|HR_E_UNEXPECTED|  
|Текст сообщения|Поставщик сообщил о непредвиденном глобальном сбое.|  
  
## <a name="explanation"></a>Объяснение  
 При обработке распределенного запроса возникла типовая ошибка при обращении к поставщику OLE DB.  
  
## <a name="user-action"></a>Действие пользователя  
 Соберите события трассировки OLE DB с помощью приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] и предоставьте эти данные службе поддержки продукта поставщика OLE DB.  
  
## <a name="see-also"></a>См. также  
 [Шаблоны и разрешения приложения SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)   
 [SQL Server Native Client (OLE DB)](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
