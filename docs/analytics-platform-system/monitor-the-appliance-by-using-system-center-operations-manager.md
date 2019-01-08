---
title: Монитор с SCOM — Analytics Platform System | Документация Майкрософт
description: Используйте System Center Operations Manager (SCOM) для мониторинга Analytics Platform System (APS) устройство.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 3c43734dbd7ef1a766f3f1258f97565ab82e175d
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2018
ms.locfileid: "52417565"
---
# <a name="monitor-with-system-center-operations-manager---analytics-platform-system"></a>Мониторинг с помощью System Center Operations Manager — система Analytics Platform System
Используйте System Center Operations Manager (SCOM) для мониторинга Analytics Platform System (APS) устройство.
  
## <a name="before-you-begin"></a>Перед началом  
  
### <a name="prerequisites"></a>предварительные требования  
  
1.  System Center Operations Manager 2007 R2, 2012 или 2012 с пакетом обновления 1 должны быть установлены и запущены.  
  
2.  Необходимо установить собственный клиент SQL Server 2008 R2 или SQL Server 2012 Native Client.  
  
3.  Пакеты управления для наблюдения за SQL Server PDW должен быть установлен, импортировать и настроен. Используйте инструкции в следующих статьях для выполнения этих задач.  
  
    -   [Установить пакеты управления SCOM &#40;Analytics Platform System&#41;](install-the-scom-management-packs.md)  
  
    -   [Импорт пакета управления SCOM для PDW &#40;Analytics Platform System&#41;](import-the-scom-management-pack-for-pdw.md) 
    
    -   [Настройка SCOM для мониторинга Analytics Platform System &#40;Analytics Platform System&#41;](configure-scom-to-monitor-analytics-platform-system.md)
  
<!-- MISSING LINKS    -   [Import the SCOM Management Pack for HDInsight &#40;Analytics Platform System&#41;](import-the-scom-management-pack-for-hdinsight.md)  -->  
   
  
## <a name="to-monitor-sql-server-pdw-with-scom"></a>Для мониторинга SQL Server PDW с SCOM  
После настройки пакетов управления SCOM, щелкните на панели мониторинга из SCOM и детализировать **SQL Server Appliance** и затем **Microsoft SQL Server Parallel Data Warehouse**. Под Microsoft SQL Server Parallel Data Warehouse имеется четыре варианта: Оповещения, устройства, устройство схемы и узлов.  
  
### <a name="alerts"></a>Предупреждения  
Оповещения создаются, где можно найти текущие оповещения для управления.  
  
![Alerts](./media/monitor-the-appliance-by-using-system-center-operations-manager/SCOM_SCOM.png "SCOM_SCOM")  
  
### <a name="appliances"></a>Устройства  
Модули являются, которой в настоящее время обнаруженных и отслеживаемых SQL Server PDW устройств можно найти в вашей среде. Если устройства не появилась здесь и создании подключения ODBC для него, то может быть проблема с вашей учетной записью PDWWatcher. Если они отображаются как «Наблюдение не ведется», может существовать проблема с вашей учетной записью PDWMonitor. Сохраняйте Терпение, поскольку SCOM не вносит изменения в режиме реального времени, но периодически проверяет наличие новых устройств для мониторинга и периодически отправляет запросы к устройствам для мониторинга.  
  
![Appliances](./media/monitor-the-appliance-by-using-system-center-operations-manager/SCOM_SCOM2.png "SCOM_SCOM2")  
  
### <a name="appliances-diagram"></a>Диаграмма устройств  
Страница устройств схема является, где можно получить краткий обзор работоспособности вашего устройства с представление в виде дерева:  
  
![Диаграмма устройств](./media/monitor-the-appliance-by-using-system-center-operations-manager/SCOM_SCOM3.png "SCOM_SCOM3")  
  
### <a name="nodes"></a>Узлы  
Наконец представление узлов дает возможность видеть работоспособность вашего устройства через каждый узел:  
  
![Nodes](./media/monitor-the-appliance-by-using-system-center-operations-manager/SCOM_SCOM4.png "SCOM_SCOM4")  
  
## <a name="see-also"></a>См. также  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
[Предупреждения консоли администрирования основные сведения о &#40;Analytics Platform System&#41;](understanding-admin-console-alerts.md)  
  
