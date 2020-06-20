---
title: Установка времени и длительности простоя ЦП (среда SQL Server Management Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- CPU [SQL Server], idle conditions
- time [SQL Server], CPU idle and duration
- duration of CPU idle [SQL Server]
- SQL Server Agent, CPU idle conditions
- idle time [SQL Server]
ms.assetid: 8647b465-d899-4cc7-9640-134a506d0a2e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1660f6d70977b8f590a18adf952a6a19f32a26cf
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85067601"
---
# <a name="set-cpu-idle-time-and-duration-sql-server-management-studio"></a>Установка времени и длительности простоя ЦП (среда SQL Server Management Studio)
  В этом разделе рассказывается о том, как задать условие простоя ЦП для сервера в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Определение простоя ЦП влияет на [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] реакцию агента на события. Например, предположим, определены такие условия простоя ЦП, что средняя загрузка ЦП не превышает 10% и остается на этом уровне в течение 10 минут. Тогда, если определены задания, которые должны выполняться при достижении ЦП сервера условий простоя, выполнение задания начнется, как только загрузка ЦП упадет ниже 10% и пробудет на этом уровне 10 минут. Если это задание существенно влияет на производительность сервера, определение условий простоя ЦП имеет очень большое значение.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-set-cpu-idle-time-and-duration"></a>Задание времени и продолжительности простоя ЦП  
  
1.  В **обозревателе объектов** подключитесь к экземпляру [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] и разверните его.  
  
2.  Щелкните правой кнопкой мыши **Агент SQL Server**, выберите **Свойства**и перейдите на страницу **Дополнительно** .  
  
3.  В области **Условие бездействия ЦП**выполните следующие действия.  
  
    -   Установите флажок **Определите условие бездействия ЦП**.  
  
    -   Укажите процент загрузки ЦП в поле **Среднее время использования ЦП сократилось до** (для всех процессоров). Так задается максимальный уровень загрузки для времени простоя ЦП.  
  
    -   Укажите количество секунд в поле **И остается ниже этого уровня в течение** . Так задается промежуток времени, в течение которого должен сохраняться минимальный уровень загрузки ЦП, чтобы считать это простоем.  
  
  
