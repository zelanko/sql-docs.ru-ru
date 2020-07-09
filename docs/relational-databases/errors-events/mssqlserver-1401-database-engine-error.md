---
title: MSSQLSERVER_1401 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 1401 (Database Engine error)
ms.assetid: 02928770-aa63-4509-8713-406c73e4cedc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0c656780c4ef64584f9ce6c28a183a9c9b821619
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85781062"
---
# <a name="mssqlserver_1401"></a>MSSQLSERVER_1401
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|SQL Server|  
|Идентификатор события|1401|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBM_MASTERSTARTUP|  
|Текст сообщения|Запуск подпрограммы основного потока зеркального отображения базы данных завершился неудачей по следующей причине: %ls. Устраните причину данной ошибки и перезапустите службу SQL Server.|  
  
## <a name="explanation"></a>Объяснение  
Запуск контрольного потока зеркального отображения завершился неудачно.  
  
## <a name="user-action"></a>Действие пользователя  
В журнале событий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] найдите сведения об ошибке, предшествующей сообщению. Устраните причину этой ошибки и перезапустите службу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (MSSQLSERVER).  
  
## <a name="see-also"></a>См. также:  
[Запуск, остановка, приостановка, возобновление и перезапуск компонента Database Engine, агента SQL и службы браузера SQL Server](~/database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)  
  
