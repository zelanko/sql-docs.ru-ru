---
title: Открытие монитора активности (среда SQL Server Management Studio) | Документация Майкрософт
ms.custom: ''
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
manager: craigg
ms.openlocfilehash: b3afa266112b29f75b7a26a0e5cb9093d2776276
ms.sourcegitcommit: cff8dd63959d7a45c5446cadf1f5d15ae08406d8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/05/2019
ms.locfileid: "67583985"
---
# <a name="open-activity-monitor-sql-server-management-studio"></a>Открытие монитора активности (среда SQL Server Management Studio)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
   
 Монитор активности выполняет запросы в отслеживаемом экземпляре, чтобы получать данные для панелей отображения монитора активности. Если установлен интервал обновления менее 10 секунд, то время, затрачиваемое на выполнение этих запросов, может повлиять на производительность сервера.  
  
  
##  <a name="Permissions"></a> Проверьте разрешения!  
 Для просмотра фактической активности вам нужно разрешение VIEW SERVER STATE. Для просмотра раздела ввода-вывода в файл данных монитора активности, кроме разрешения на VIEW SERVER STATE, необходимо иметь также разрешения на CREATE DATABASE, ALTER ANY DATABASE или VIEW ANY DEFINITION.  
  
 Для вызова инструкции KILL для процесса пользователь должен быть членом предопределенных ролей сервера sysadmin или processadmin.  
  
  
## <a name="open-activity-monitor"></a>Открытие монитора активности  

### <a name="keyboard-shortcut"></a>Сочетание клавиш  
 - Нажмите клавиши **CTRL+ALT+A** , чтобы открыть монитор активности в любое время.

 >**Подсказка.** Наведите указатель мыши на значок в SSMS, чтобы узнать, что это за функция и какое сочетание клавиш активирует ее.

### <a name="toolbar"></a>Панель инструментов

На стандартной панели инструментов щелкните значок **Монитор активности** . Он находится в середине, справа от кнопок отмены и повтора.
![Activity_Monitor_icon](../../relational-databases/performance-monitor/media/activity-monitor-icon.png)  
  
Заполните данные в диалоговом окне **Соединение с сервером** , если вы еще не подключены к экземпляру SQL Server, которые требуется отслеживать.
  
## <a name="launch-activity-monitor-and-object-explorer-on-startup"></a>Открытие монитора активности и обозревателя объектов при запуске
  
1.  В меню **Сервис** щелкните пункт **Параметры**.  
  
2.  В диалоговом окне **Параметры** разверните узел **Среда**и выберите **Запуск**.  
  
3.  В раскрывающемся списке **При запуске** выберите **Открыть обозреватель объектов и монитор активности**.  

4.  Нажмите кнопку **ОК**.

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

![open_object_explorer](../../relational-databases/performance-monitor/media/open-object-explorer.png)
  
  
## <a name="set-the-activity-monitor-refresh-interval"></a>Задание интервала обновления монитора активности  
  
1.   Откройте монитор активности.  
  
2.   Щелкните правой кнопкой мыши пункт **Обзор**, выберите пункт **Интервал обновления**, а затем — интервал, в котором монитор активности будет получать новые данные экземпляра.  
  
  
