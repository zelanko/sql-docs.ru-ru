---
title: Настройка политик исправности (служебная программа SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 030aac3b-8901-4c41-91ed-aba96420276c
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: da394108767b6d6583bbf185bcc1c3a699051ed6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48062870"
---
# <a name="configure-health-policies-sql-server-utility"></a>Настройка политик исправности (служебная программа SQL Server)
  Панель мониторинга программы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] позволяет просмотреть параметры программы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для управляемых экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и приложений уровня данных. Дополнительные сведения см. в разделе [Функции и задачи служебной программы SQL Server](sql-server-utility-features-and-tasks.md).  
  
 Чтобы просмотреть результаты политики исправности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , подключитесь к точке управления служебной программой из среды [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Дополнительные сведения см. в статье [Использование проводника служебных программ для управления служебной программой SQL Server](use-utility-explorer-to-manage-the-sql-server-utility.md).  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Политики исправности программы можно настроить для приложений уровня данных и экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. В программе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] политика исправности может быть задана глобально для всех приложений уровня данных и управляемых экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , либо ее можно задать индивидуально для отдельных приложений уровня данных и управляемых экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в программе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="monitoring-policies-for-data-tier-applications"></a>Политики наблюдения для приложений уровня данных  
 Политики чрезмерного и недостаточного использования для приложений уровня данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
-   Загрузка процессора приложением уровня данных.  
  
-   Файловое пространство приложения уровня данных для файлов баз данных.  
  
-   Файловое пространство приложения уровня данных для томов хранилища.  
  
-   Использование процессора компьютера.  
  
> [!NOTE]  
>  Для приложений уровня данных использование томов хранилища и процессора является политиками только для чтения.  
  
 Дополнительные сведения о просмотре или изменении глобальных политик наблюдения для приложений уровня данных см. в статье [Администрирование программ (служебная программа SQL Server)](../../database-engine/utility-administration-sql-server-utility.md).  
  
 Дополнительные сведения о просмотре и изменении политик наблюдения для отдельных приложений уровня данных см. в статье [Подробные сведения о развернутом приложении уровня данных (служебная программа SQL Server)](../../database-engine/deployed-data-tier-application-details-sql-server-utility.md).  
  
## <a name="monitoring-policies-for-managed-instances-of-sql-server"></a>Политики наблюдения для управляемых экземпляров SQL Server  
 Политики чрезмерного и недостаточного использования для управляемых экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для файлов баз данных.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для томов хранилища.  
  
-   Использование процессора компьютера.  
  
 Дополнительные сведения о просмотре или изменении глобальных политик наблюдения для управляемых экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в статье [Администрирование программ (служебная программа SQL Server)](../../database-engine/utility-administration-sql-server-utility.md).  
  
 Дополнительные сведения о просмотре и изменении политик наблюдения для отдельных управляемых экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в статье [Подробные сведения о развернутом приложении уровня данных (служебная программа SQL Server)](../../database-engine/managed-instance-details-sql-server-utility.md).  
  
## <a name="see-also"></a>См. также  
 [Функции и задачи служебной программы SQL Server](sql-server-utility-features-and-tasks.md)   
 [Уменьшение уровня шума в политиках загрузки ЦП (служебная программа SQL Server)](reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)  
  
  
