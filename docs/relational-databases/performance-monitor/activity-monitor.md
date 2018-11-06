---
title: Монитор активности | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance-monitor
ms.topic: conceptual
helpviewer_keywords:
- Activity Monitor [SQL Server]
ms.assetid: 1e6c430d-3a2a-468e-a3d5-ef5459c36c15
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: cc0a42cb38ca6ca3d4382b6abd293e93fd04ff16
ms.sourcegitcommit: af1d9fc4a50baf3df60488b4c630ce68f7e75ed1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/06/2018
ms.locfileid: "51029971"
---
# <a name="activity-monitor"></a>Монитор активности
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Монитор активности отображает сведения о процессах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и о том, как функционирование этих процессов влияет на текущий экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Монитор активности — это окно документов с вкладками со следующими развертываемыми и свертываемыми панелями: **Общие сведения**, **Активные пользовательские задачи**, **Ожидающие ресурсов**, **Ввод-вывод в файл данных**и **Последние ресурсоемкие запросы**. После развертывания любой панели монитор активности выполняет запрос к экземпляру для получения необходимых сведений. При свертывании панели выполнение всех операций запроса для этой панели приостанавливается. Можно одновременно развернуть одну или более панелей для просмотра различных типов активности в экземпляре.  
 
 ## <a name="customize-columns"></a>Настройка столбцов 
 Для столбцов на панели **Активные пользовательские задачи**, **Ожидание ресурсов**, **Ввод-вывод в файл данных**или **Последние ресурсоемкие запросы** можно настроить отображение следующим образом:  
  
1.  Чтобы изменить порядок столбцов, щелкните заголовок столбца и перетащите его в другое место ленты заголовков.  
  
2.  Чтобы отсортировать столбец, щелкните имя столбца.  
  
3.  Чтобы выполнить фильтрацию по одному или нескольким столбцам, щелкните стрелку раскрывающегося списка в заголовке столбца и выберите значение.  
  
## <a name="more-information"></a>Дополнительные сведения  
   
|||  
|-|-|  
|Содержит сведения о том, как открыть монитор активности и настроить интервал обновления монитора активности.|[Открытие монитора активности (среда SQL Server Management Studio)](../../relational-databases/performance-monitor/open-activity-monitor-sql-server-management-studio.md)|  
|Ссылки на разделы с описанием производительности сервера и отслеживания действий.|[Производительность сервера и мониторинг активности](../../relational-databases/performance/server-performance-and-activity-monitoring.md)|  
  
  
