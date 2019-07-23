---
title: Монитор активности | Документация Майкрософт
ms.custom: ''
ms.date: 04/07/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Activity Monitor [SQL Server]
ms.assetid: 1e6c430d-3a2a-468e-a3d5-ef5459c36c15
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 05a034bfb174ef3a1d7240bd1d8a3607e9001ddb
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68024842"
---
# <a name="activity-monitor"></a>Монитор активности
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Монитор активности отображает сведения о процессах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и о том, как функционирование этих процессов влияет на текущий экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Монитор активности — это окно документов с вкладками со следующими развертываемыми и свертываемыми панелями: **Обзор**, **Процессы**, **Ожидающие ресурсы**, **Ввод-вывод в файл данных**, **Последние ресурсоемкие запросы** и **Активные ресурсоемкие запросы**. После развертывания любой панели монитор активности выполняет запрос к экземпляру для получения необходимых сведений. При свертывании панели выполнение всех операций запроса для этой панели приостанавливается. Можно одновременно развернуть одну или более панелей для просмотра различных типов активности в экземпляре.  
 
## <a name="customize-columns"></a>Настройка столбцов 
Для столбцов на панели **Процессы**, **Ожидающие ресурсы**, **Ввод-вывод в файл данных**, **Последние ресурсоемкие запросы** и **Активные ресурсоемкие запросы** можно настроить отображение следующим образом:  
  
1.  Чтобы изменить порядок столбцов, щелкните заголовок столбца и перетащите его в другое место ленты заголовков.  
  
2.  Чтобы отсортировать столбец, щелкните имя столбца.  
  
3.  Чтобы выполнить фильтрацию по одному или нескольким столбцам, щелкните стрелку раскрывающегося списка в заголовке столбца и выберите значение.  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

## <a name="more-information"></a>Дополнительные сведения  
   
|||  
|-|-|  
|Содержит сведения о том, как открыть монитор активности и настроить интервал обновления монитора активности.|[Открытие монитора активности (среда SQL Server Management Studio)](../../relational-databases/performance-monitor/open-activity-monitor-sql-server-management-studio.md)|  
|Ссылки на разделы с описанием производительности сервера и отслеживания действий.|[Производительность сервера и мониторинг активности](../../relational-databases/performance/server-performance-and-activity-monitoring.md)|  
  
  
