---
title: Монитор с SCOM - система платформы аналитики | Документы Microsoft
description: System Center Operations Manager (SCOM) используется для мониторинга устройства Analytics Platform System (APS).
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: c2b26462ab37cf7d63960ff7db6e20c57e8290bb
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
ms.locfileid: "31538984"
---
# <a name="monitor-with-system-center-operations-manager---analytics-platform-system"></a>Монитор с System Center Operations Manager — система платформы аналитики
System Center Operations Manager (SCOM) используется для мониторинга устройства Analytics Platform System (APS).
  
## <a name="before-you-begin"></a>Перед началом  
  
### <a name="prerequisites"></a>предварительные требования  
  
1.  System Center Operations Manager 2007 R2, 2012 или 2012 с пакетом обновления 1 должны быть установлены и запущены.  
  
2.  Должен быть установлен собственный клиент SQL Server 2008 R2 или SQL Server 2012 Native Client.  
  
3.  Пакеты управления для наблюдения за SQL Server PDW и HDInsight должен быть установлен, импортированные и настроенные. Используйте следующие статьи инструкции для выполнения следующих задач.  
  
    -   [Установить пакеты управления SCOM &#40;система платформы аналитики&#41;](install-the-scom-management-packs.md)  
  
    -   [Импорт пакета управления SCOM для PDW &#40;система платформы аналитики&#41;](import-the-scom-management-pack-for-pdw.md) 
    
    -   [Настройка SCOM для наблюдения за Analytics Platform System &#40;система платформы аналитики&#41;](configure-scom-to-monitor-analytics-platform-system.md)
  
<!-- MISSING LINKS    -   [Import the SCOM Management Pack for HDInsight &#40;Analytics Platform System&#41;](import-the-scom-management-pack-for-hdinsight.md)  -->  
   
  
## <a name="to-monitor-sql-server-pdw-with-scom"></a>Для мониторинга SQL Server PDW с SCOM  
После настройки пакетов управления SCOM, щелкните на панели мониторинга из SCOM и детализации углублением до **устройстве SQL Server** и затем **Microsoft SQL Server Parallel Data Warehouse**. Под Microsoft SQL Server Parallel Data Warehouse, существует четыре варианта: оповещения, устройства, схема устройства и узлы.  
  
### <a name="alerts"></a>Предупреждения  
Оповещения —, где можно найти текущие оповещения для управления.  
  
![Alerts](./media/monitor-the-appliance-by-using-system-center-operations-manager/SCOM_SCOM.png "SCOM_SCOM")  
  
### <a name="appliances"></a>Устройства  
Устройства будут которой можно найти в настоящее время обнаруженных и отслеживаемых SQL Server PDW устройств в вашей среде. Если устройство не отображаться здесь и создания соединения ODBC для него, затем может существовать проблема с вашей учетной записью PDWWatcher. Если они отображаются как «Наблюдение не ведется», может существовать проблема с вашей учетной записью PDWMonitor. Наберитесь терпения, так как SCOM не вносит изменения в режиме реального времени, но периодически проверяет новые приложения для мониторинга и периодически отправляет запросы на устройства для наблюдения.  
  
![Appliances](./media/monitor-the-appliance-by-using-system-center-operations-manager/SCOM_SCOM2.png "SCOM_SCOM2")  
  
### <a name="appliances-diagram"></a>Диаграмма устройств  
Страница схемы устройств является, где можно получить представление работоспособности устройства с представление в виде дерева:  
  
![Диаграмма устройств](./media/monitor-the-appliance-by-using-system-center-operations-manager/SCOM_SCOM3.png "SCOM_SCOM3")  
  
### <a name="nodes"></a>Узлы  
Наконец представление узлов позволяет проверять работоспособность устройства через каждого узла:  
  
![Nodes](./media/monitor-the-appliance-by-using-system-center-operations-manager/SCOM_SCOM4.png "SCOM_SCOM4")  
  
## <a name="see-also"></a>См. также  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
[Предупреждения консоли администрирования основные сведения о &#40;система платформы аналитики&#41;](understanding-admin-console-alerts.md)  
  
