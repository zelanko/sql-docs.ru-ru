---
title: Монитор устройств с помощью System Center Operations Manager (APS)
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.technology: mpp-data-warehouse
ms.custom: ''
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: de6cbf6e-f2e9-4877-94df-9c13b1182d56
caps.latest.revision: 14
ms.openlocfilehash: 02bdd22c66729ab471298e211b619e1cb1e4565c
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
# <a name="monitor-the-appliance-by-using-system-center-operations-manager"></a>Мониторинг устройства с помощью System Center Operations Manager
Здесь описывается, как использовать System Center Operations Manager для наблюдения за SQL Server PDW и HDInsight.  
  
## <a name="before-you-begin"></a>Перед началом  
  
### <a name="prerequisites"></a>предварительные требования  
  
1.  System Center Operations Manager 2007 R2, 2012 или 2012 с пакетом обновления 1 должны быть установлены и запущены.  
  
2.  Должен быть установлен собственный клиент SQL Server 2008 R2 или SQL Server 2012 Native Client.  
  
3.  Пакеты управления для наблюдения за SQL Server PDW и HDInsight должен быть установлен, импортированные и настроенные. Используйте следующие инструкции для выполнения следующих задач.  
  
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
Устройства будут которой можно найти в настоящее время обнаруженных и отслеживаемых SQL Server PDW устройств в вашей среде. Если устройство не отображаться здесь и создания соединения ODBC для него, затем может существовать проблема с вашей учетной записью PDWWatcher. Если они отображаются как «Неотслеживаемые» может существовать проблема с вашей учетной записью PDWMonitor. Наберитесь терпения SCOM не вносит изменения в режиме реального времени, но периодически проверяет новые приложения для мониторинга и периодически отправляет запросы на устройства для наблюдения.  
  
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
  
