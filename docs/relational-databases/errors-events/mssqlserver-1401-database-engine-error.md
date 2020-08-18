---
description: MSSQLSERVER_1401
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
ms.openlocfilehash: cc47816715273a60fb49f1d209e4d531c205c5aa
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88335210"
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
  
