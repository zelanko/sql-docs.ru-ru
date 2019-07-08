---
title: Просмотр результатов действия политики исправности ресурсов (служебная программа SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 80cb14fb-f4c6-4be2-ba17-eb4e4cddd35f
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 932b9e095f6f5893bba985e49881ff8c758bd499
ms.sourcegitcommit: cff8dd63959d7a45c5446cadf1f5d15ae08406d8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/05/2019
ms.locfileid: "67580820"
---
# <a name="view-resource-health-policy-results-sql-server-utility"></a>Просмотр результатов политики исправности ресурсов (служебная программа SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Панель мониторинга служебной программы в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] позволяет просмотреть параметры служебной программы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для управляемых экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и приложений уровня данных. Дополнительные сведения см. в разделе [Функции и задачи служебной программы SQL Server](../../relational-databases/manage/sql-server-utility-features-and-tasks.md).  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="view-sql-server-utility-resource-health-policy-results"></a>Просмотр результатов политики исправности ресурсов (SQL Server Utility)  
  
1.  В меню [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Вид **среды**(SSMS) выберите пункт **Обозреватель программы** , чтобы открыть панель навигации проводника служебной программы. Чтобы открыть панель содержимого, в меню **Вид**выберите пункт **Содержимое обозревателя программ**.  
  
2.  На панели навигации щелкните ![](../../relational-databases/manage/media/connect-to-utility.gif "Соединение со служебной программой")**Соединение со служебной программой**. Если точка управления служебной программой еще не создана либо экземпляры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или приложения уровня данных не зарегистрированы в служебной программе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , см. раздел [Функции и задачи служебной программы SQL Server](../../relational-databases/manage/sql-server-utility-features-and-tasks.md).  
  
3.  Щелкните узел точки управления служебной программой, чтобы отобразить сводные данные по управляемым экземплярам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и приложениям уровня данных (щелкните правой кнопкой мыши, чтобы выполнить обновление). Данные панели мониторинга отображаются в области содержимого.  
  
4.  Щелкните узел **Управляемые экземпляры** , чтобы открыть список данных по управляемым экземплярам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (щелкните его правой кнопкой мыши, чтобы выполнить обновление). Данные в представлении списка отображаются на панели содержимого.  
  
5.  Щелкните узел **Развернутые приложения уровня данных** , чтобы отобразить список данных по приложениям уровня данных (щелкните его правой кнопкой мыши, чтобы выполнить обновление). Данные в представлении списка отображаются на панели содержимого.  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

## <a name="see-also"></a>См. также:  
 [Функции и задачи служебной программы SQL Server](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)   
 [Уменьшение уровня шума в политиках загрузки ЦП (служебная программа SQL Server)](../../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)   
 [Подробные сведения о развернутом приложении уровня данных (служебная программа SQL Server)](https://msdn.microsoft.com/library/79c41dd9-abcb-434e-9326-00a341d5c867)   
 [Подробные сведения об управляемом экземпляре (служебная программа SQL Server)](https://msdn.microsoft.com/library/6e51b7bb-a733-4852-8c33-7f4dbdf931c2)   
 [Администрирование программ (служебная программа SQL Server)](https://msdn.microsoft.com/library/3e5a00c3-8905-40f0-9ddc-d924df9c2f0d)  
  
  
