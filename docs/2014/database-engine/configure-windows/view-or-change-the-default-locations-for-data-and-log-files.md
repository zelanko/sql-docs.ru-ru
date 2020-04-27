---
title: Просмотр или изменение расположения по умолчанию для файлов данных и журналов (SQL Server Management Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- log files [SQL Server], changing default location
- data files [SQL Server], changing default location
ms.assetid: 70a57fda-fcfe-490f-9cf6-5df620e32b2a
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 06d17a4feaec0db614f61fb7761b37ea415efc24
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62808715"
---
# <a name="view-or-change-the-default-locations-for-data-and-log-files-sql-server-management-studio"></a>Просмотр или изменение расположения по умолчанию для файлов данных и журнала (среда SQL Server Management Studio)
  Данный раздел описывает функции просмотра и изменения расположения по умолчанию для новых файлов данных и файлов журнала в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Путь по умолчанию берется из реестра. После изменения местоположения все новые базы данных, созданные в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , будут использовать это местоположение, если не указано другое местоположение.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Рекомендации](#Recommendations)  
  
-   **Просмотр или изменение местоположения по умолчанию для файлов данных и журналов с использованием следующих средств:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
-   **Продолжение**  [после изменения расположений по умолчанию](#FollowUp)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Рекомендации  
 Рекомендуемым способом защиты файлов данных и журналов является защита с помощью списков управления доступом (ACL). Списки ACL должны располагаться в корневом каталоге, в котором создаются файлы.  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-view-or-change-the-default-locations-for-database-files"></a>Просмотр или изменение расположения по умолчанию для файлов базы данных  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши сервер и выберите **Свойства**.  
  
2.  На левой панели щелкните страницу **Параметры базы данных** .  
  
3.  В области **Места хранения, используемые базой данных по умолчанию**можно просмотреть текущие расположения, используемые по умолчанию для новых файлов данных и файлов журнала. Чтобы изменить местоположение по умолчанию, введите новый путь по умолчанию в поле **Данные** или **Журнал** или нажмите кнопку обзора, перейдите к нужному пути и выберите его.  
  
##  <a name="follow-up-after-changing-the-default-locations"></a><a name="FollowUp"></a>Дальнейшие действия. После изменения расположений по умолчанию  
 Необходимо остановить и запустить службу SQL Server для завершения изменения.  
  
## <a name="see-also"></a>См. также  
 [CREATE DATABASE (SQL Server Transact-SQL)](/sql/t-sql/statements/create-database-sql-server-transact-sql)   
 [Создание базы данных](../../relational-databases/databases/create-a-database.md)  
  
  
