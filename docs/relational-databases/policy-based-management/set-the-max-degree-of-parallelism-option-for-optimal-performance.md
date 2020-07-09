---
title: Максимальная степень параллелизма и управление на основе политик
description: Описывает настройку политики для проверки максимальной степени параллелизма для управления на основе политик для SQL Server.
ms.custom: seo-lt-2019
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: ec908006-67ae-4674-9a61-25ea741d6197
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 9f2cd688ca16baad21ec295105eeb0fdbbbda967
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85774184"
---
# <a name="set-the-max-degree-of-parallelism-option-for-optimal-performance"></a>Задание параметра максимальной степени параллелизма для оптимальной производительности
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Это правило определяет, является ли значение параметра максимальной степени параллелизма (MAXDOP) больше 8. Установка большего значения часто приводит к неэффективному расходованию ресурсов и снижению производительности.  
  
## <a name="best-practice-recommendations"></a>Рекомендации  
 Параметр конфигурации max degree of parallelism (MAXDOP) определяет количество процессоров, используемых для выполнения запроса в параллельном плане. Этот параметр определяет количество потоков, используемых для операторов плана запроса, выполняющих работу параллельно. В зависимости от того, настраивается ли SQL Server на симметричном многопроцессорном компьютере (SMP), на компьютере с неоднородным доступом к памяти (NUMA) или процессорах с поддержкой технологии Hyper-Threading, необходимо соответствующим образом настроить параметр максимальной степени параллелизма. 
 
 Рекомендации по настройке MAXDOP зависят от используемой версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Рекомендации по конкретным версиям см. в разделе [Настройка параметра конфигурации сервера max degree of parallelism](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md#Guidelines); также настройте политику для проверки значения максимальной степени параллелизма соответствующим образом.     
  
## <a name="for-more-information"></a>Дополнительные сведения  
 [Рекомендации и инструкции по использованию параметра конфигурации max degree of parallelism в SQL Server](https://go.microsoft.com/fwlink/?linkid=117786)    
 [Настройка параметра конфигурации сервера max degree of parallelism](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md#Guidelines)     
 [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)     
  
