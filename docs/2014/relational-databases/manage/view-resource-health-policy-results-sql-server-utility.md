---
title: Просмотр результатов действия политики исправности ресурсов (служебная программа SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 80cb14fb-f4c6-4be2-ba17-eb4e4cddd35f
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 52137a6405090ca52f3a99f21b400a573e606dc0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63065583"
---
# <a name="view-resource-health-policy-results-sql-server-utility"></a>Просмотр результатов политики исправности ресурсов (служебная программа SQL Server)
  Панель мониторинга служебной программы в среде [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] позволяет просмотреть параметры служебной программы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для управляемых экземпляров [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и приложений уровня данных. Дополнительные сведения см. в разделе [Функции и задачи служебной программы SQL Server](sql-server-utility-features-and-tasks.md).  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="view-sql-server-utility-resource-health-policy-results"></a>Просмотр результатов политики исправности ресурсов (SQL Server Utility)  
  
1.  В меню [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Вид **среды**(SSMS) выберите пункт **Обозреватель программы** , чтобы открыть панель навигации проводника служебной программы. Чтобы открыть панель содержимого, в меню **Вид**выберите пункт **Содержимое обозревателя программ**.  
  
2.  На панели навигации щелкните ![](../../database-engine/media/connect-to-utility.gif "Connect_to_Utility")**Соединение со служебной программой**. Если точка управления служебной программой еще не создана либо экземпляры [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] или приложения уровня данных не зарегистрированы в служебной программе [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , см. раздел [Функции и задачи служебной программы SQL Server](sql-server-utility-features-and-tasks.md).  
  
3.  Щелкните узел точки управления служебной программой, чтобы отобразить сводные данные по управляемым экземплярам [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и приложениям уровня данных (щелкните правой кнопкой мыши, чтобы выполнить обновление). Данные панели мониторинга отображаются в области содержимого.  
  
4.  Щелкните узел **Управляемые экземпляры** , чтобы открыть список данных по управляемым экземплярам [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (щелкните его правой кнопкой мыши, чтобы выполнить обновление). Данные в представлении списка отображаются на панели содержимого.  
  
5.  Щелкните узел **Развернутые приложения уровня данных** , чтобы отобразить список данных по приложениям уровня данных (щелкните его правой кнопкой мыши, чтобы выполнить обновление). Данные в представлении списка отображаются на панели содержимого.  
  
## <a name="see-also"></a>См. также:  
 [Функции и задачи служебной программы SQL Server](sql-server-utility-features-and-tasks.md)   
 [Уменьшение уровня шума в политиках загрузки ЦП (служебная программа SQL Server)](reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)   
 [Подробные сведения о развернутом приложении уровня данных (служебная программа SQL Server)](../../database-engine/deployed-data-tier-application-details-sql-server-utility.md)   
 [Подробные сведения об управляемом экземпляре (служебная программа SQL Server)](../../database-engine/managed-instance-details-sql-server-utility.md)   
 [Администрирование программ (служебная программа SQL Server)](../../database-engine/utility-administration-sql-server-utility.md)  
  
  
