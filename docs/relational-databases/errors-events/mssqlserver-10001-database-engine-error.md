---
description: MSSQLSERVER_10001
title: MSSQLSERVER_10001 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10001 (Database Engine error)
ms.assetid: f8fd2d8d-a4af-4b6a-ba51-9123b7e4c9bf
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4aedbaa7b1d5224bb09b71ccdff4866e350ee691
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88339630"
---
# <a name="mssqlserver_10001"></a>MSSQLSERVER_10001
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|SQL Server|  
|Идентификатор события|10001|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|HR_E_UNEXPECTED|  
|Текст сообщения|Поставщик сообщил о непредвиденном глобальном сбое.|  
  
## <a name="explanation"></a>Объяснение  
При обработке распределенного запроса возникла типовая ошибка при обращении к поставщику OLE DB.  
  
## <a name="user-action"></a>Действие пользователя  
Соберите события трассировки OLE DB с помощью приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] и предоставьте эти данные службе поддержки продукта поставщика OLE DB.  
  
## <a name="see-also"></a>См. также:  
[Шаблоны и разрешения приложения SQL Server Profiler](~/tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)  
[SQL Server Native Client (OLE DB)](~/relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
