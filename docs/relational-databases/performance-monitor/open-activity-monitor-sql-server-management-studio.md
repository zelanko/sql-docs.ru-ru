---
title: Открытие монитора активности (SSMS)
description: Как открыть монитор активности в среде SQL Server Management Studio (SSMS).
ms.custom: seo-dt-2019
ms.date: 08/05/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Activity Monitor [SQL Server], setting the refresh interval
- refresh interval for Activity Monitor
- Activity Monitor [SQL Server], opening
- opening Activity Monitor
ms.assetid: 0a6eeb16-f02b-479d-9a60-543e40ebf46b
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 16d08bbc2b651ef21ee80be1e8af74a00b45a253
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85787439"
---
# <a name="open-activity-monitor-in-sql-server-management-studio-ssms"></a>Открытие монитора активности в среде SQL Server Management Studio (SSMS)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
   
 Монитор активности выполняет запросы в отслеживаемом экземпляре, чтобы получать данные для панелей отображения монитора активности. Если установлен интервал обновления менее 10 секунд, то время, затрачиваемое на выполнение этих запросов, может повлиять на производительность сервера.  
  
  
##  <a name="check-your-permissions"></a><a name="Permissions"></a> Проверьте разрешения!  
 Для просмотра фактической активности вам нужно разрешение VIEW SERVER STATE. Для просмотра раздела ввода-вывода в файл данных монитора активности, кроме разрешения на VIEW SERVER STATE, необходимо иметь также разрешения на CREATE DATABASE, ALTER ANY DATABASE или VIEW ANY DEFINITION.  
  
 Для вызова инструкции KILL для процесса пользователь должен быть членом предопределенных ролей сервера sysadmin или processadmin.  
  
  
## <a name="open-activity-monitor"></a>Открытие монитора активности  

### <a name="keyboard-shortcut"></a>Сочетания клавиш  
 - Нажмите клавиши **CTRL+ALT+A** , чтобы открыть монитор активности в любое время.

 >**Подсказка.** Наведите указатель мыши на значок в SSMS, чтобы узнать, что это за функция и какое сочетание клавиш активирует ее.

### <a name="toolbar"></a>Панель инструментов

На стандартной панели инструментов щелкните значок **Монитор активности** . Он находится в середине, справа от кнопок отмены и повтора.
![Activity_Monitor_icon](../../relational-databases/performance-monitor/media/activity-monitor-icon.png)  
  
Заполните данные в диалоговом окне **Соединение с сервером** , если вы еще не подключены к экземпляру SQL Server, которые требуется отслеживать.
  
## <a name="launch-activity-monitor-and-object-explorer-on-startup"></a>Открытие монитора активности и обозревателя объектов при запуске
  
1.  В меню **Сервис** щелкните пункт **Параметры**.  
  
2.  В диалоговом окне **Параметры** разверните узел **Среда** и выберите **Запуск**.  
  
3.  В раскрывающемся списке **При запуске** выберите **Открыть обозреватель объектов и монитор активности**.  

4.  Нажмите кнопку **ОК**.

![open_object_explorer](../../relational-databases/performance-monitor/media/open-object-explorer.png)
  
  
## <a name="set-the-activity-monitor-refresh-interval"></a>Задание интервала обновления монитора активности  
  
1.   Откройте монитор активности.  
  
2.   Щелкните правой кнопкой мыши пункт **Обзор**, выберите пункт **Интервал обновления**, а затем — интервал, в котором монитор активности будет получать новые данные экземпляра.  
  
  
