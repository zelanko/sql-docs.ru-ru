---
title: Реплика доступности отключена | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.arp2connected.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 1a2162d3-54fb-4356-b349-effbdc15a5a4
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0ead368dece8a0c1effd8f8ddc7ff5e5793e8350
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62791858"
---
# <a name="availability-replica-is-disconnected"></a>Реплика доступности отключена
    
## <a name="introduction"></a>Введение  
  
|||  
|-|-|  
|**Имя политики**|Состояние соединения с репликами доступности|  
|**Issue**|Реплика доступности отключена.|  
|**Категория**|**Critical**|  
|**Устанавливают**|реплика доступности|  
  
## <a name="description"></a>Description  
 Эта политика проверяет состояние соединения между репликами доступности. Эта политика находится в нерабочем состоянии, если подключение к реплике доступности имеет состояние DISCONNECTED. В остальном политика находится в рабочем состоянии.  
  
> [!NOTE]  
>  Для этого выпуска [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]сведения о возможных причинах проблем и решениях доступны в разделе [Реплика доступности отключена](https://go.microsoft.com/fwlink/p/?LinkId=220857) в TechNet Wiki.  
  
## <a name="possible-causes"></a>Возможные причины  
 Вторичная реплика не подключена к первичной реплике. Состояние соединения — DISCONNECTED. Возможны следующие причины этой проблемы.  
  
-   Порт подключения может конфликтовать с другим приложением.  
  
-   Несоответствие типа или алгоритма шифрования.  
  
-   Конечная точка подключения была удалена или не была запущена.  
  
-   Транспорт отключен.  
  
## <a name="possible-solutions"></a>Возможные решения  
 Ниже перечислены возможные решения этой проблемы:  
  
-   Проверьте конфигурацию конечной точки зеркального отображения базы данных для экземпляров первичной и вторичной реплики и обновите конфигурацию с несоответствием.  
  
-   Проверьте наличие конфликта портов и при его обнаружении измените номер порта.  
  
## <a name="see-also"></a>См. также:  
 [Общие сведения о группы доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Использование панели мониторинга AlwaysOn &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
