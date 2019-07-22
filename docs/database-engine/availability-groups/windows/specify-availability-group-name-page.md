---
title: Страница "Указание параметров группы доступности" (мастер группы доступности) — SQL Server | Документация Майкрософт
ms.description: Describes the options found on the 'Specify Availability Group Name' page of the Availability Group Wizard within SQL Server Management Studio.
ms.custom: seodec18
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql13.swb.newagwizard.specifyagname.f1
- sql13.swb.adddatabasewizard.specifyagname.f1
ms.assetid: dcb6374d-becb-4c6c-b88c-5a8273f8aa38
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: da34edca55f4f21c3323e621eecf2aa6983cbf79
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68014025"
---
# <a name="specify-availability-group-options-page-for-an-always-on-availability-group"></a>Страница "Указание параметров группы доступности" группы доступности Always On
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В этом разделе описываются параметры страницы **Указание имени группы доступности** . Эта тема относится как к [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] , так и к [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
##  <a name="PageOptions"></a> Указание параметров группы доступности  
 **Имя группы доступности**  
 Укажите имя группы доступности. Для новой группы доступности укажите допустимый идентификатор [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], уникальный во всех группах доступности в отказоустойчивом кластере Windows Server (WSFC). Максимальная длина имени группы доступности составляет 128 символов.  

 **Тип кластера**. Затем укажите тип кластера. Возможные типы кластера зависят от версии [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и ОС. Выберите один из следующего списка:

   * **Кластер WSFC**
   
      Используйте, если группа доступности размещается на экземплярах [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], принадлежащих отказоустойчивому кластеру Windows Server, для обеспечения высокой доступности и аварийного восстановления. Применяется ко всем поддерживаемым версиям [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. 

   * **EXTERNAL**
      
      Используйте, если группа доступности размещается на экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] под управлением технологии внешних кластеров, для обеспечения высокой доступности и аварийного восстановления, например Pacemaker в Linux. Применяется к [!INCLUDE[sssqlv14](../../../includes/sssqlv14-md.md)] и более поздним версиям.

   * **NONE**
      
      Используйте, если группа доступности размещается на экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], который не управляется технологией кластера для масштабирования при чтении и балансировке нагрузки. Применяется к [!INCLUDE[sssqlv14](../../../includes/sssqlv14-md.md)] и более поздним версиям. 
 
   **Определение уровня работоспособности уровня базы данных**. Установите этот флажок, чтобы включить параметр определения уровня работоспособности базы данных (DB_FAILOVER) для группы доступности. Функция определения работоспособности баз данных замечает, когда база данных выходит из сетевого режима, в случае если возникают какие-либо неполадки, и инициирует автоматический переход группы доступности на другой ресурс. См. статью [SQL Server Always On Database Health Detection Failover Option](sql-server-always-on-database-health-detection-failover-option.md) (Параметр определения уровня работоспособности базы данных группы доступности).


Select Databases Page (New Availability Group Wizard and Add Database Wizard)  
  
##  <a name="LaunchWiz"></a> Связанные задачи  
  
-   [Использование диалогового окна "Создание группы доступности" (среда SQL Server Management Studio)](../../../database-engine/availability-groups/windows/use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [Использование мастера добавления базы данных в группу доступности (среда SQL Server Management Studio)](../../../database-engine/availability-groups/windows/availability-group-add-database-to-group-wizard.md)  
  
## <a name="see-also"></a>См. также:  
 [Обзор групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)  
  
