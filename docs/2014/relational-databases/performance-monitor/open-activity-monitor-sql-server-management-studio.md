---
title: Открытие монитора активности (среда SQL Server Management Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Activity Monitor [SQL Server], setting the refresh interval
- refresh interval for Activity Monitor
- Activity Monitor [SQL Server], opening
- opening Activity Monitor
ms.assetid: 0a6eeb16-f02b-479d-9a60-543e40ebf46b
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 0d1c0312acfcd2e5dbb17d740fe2659cb8c91bbe
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63032008"
---
# <a name="open-activity-monitor-sql-server-management-studio"></a>Открытие монитора активности (среда SQL Server Management Studio)
  В этом разделе описано, как можно открыть монитор активности, который позволяет получить сведения о процессах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и о том, как эти процессы влияют на текущий экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Кроме того, он описывает, как можно задать интервал обновления для монитора активности.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [безопасность](#Security)  
  
-   **Открытие монитора активности с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
-   **Чтобы задать интервал обновления с помощью:**  [SQL Server Management Studio](#Refresh)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
 Монитор активности выполняет запросы в отслеживаемом экземпляре, чтобы получать данные для панелей отображения монитора активности. Если установлен интервал обновления менее 10 секунд, то время, затрачиваемое на выполнение этих запросов, может повлиять на производительность сервера.  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Для просмотра монитора активности у пользователя должно быть разрешение VIEW SERVER STATE. Для просмотра раздела ввода-вывода в файл данных монитора активности, кроме разрешения на VIEW SERVER STATE, необходимо иметь также разрешения на CREATE DATABASE, ALTER ANY DATABASE или VIEW ANY DEFINITION.  
  
 Для вызова инструкции KILL для процесса пользователь должен быть членом предопределенных ролей сервера sysadmin или processadmin.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-open-activity-monitor-in-sql-server-management-studio"></a>Открытие монитора активности в среде SQL Server Management Studio  
  
1.  На стандартной панели инструментов среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] щелкните **Монитор активности**.  
  
2.  В диалоговом окне **Подключение к серверу** выберите имя сервера и режим проверки подлинности, а затем нажмите кнопку **Соединить**.  
  
 Открыть монитор активности можно также в любое время, нажав сочетание CTRL+ALT A.  
  
#### <a name="to-open-activity-monitor-in-object-explorer"></a>Открытие монитора активности в обозревателе объектов  
  
-   В обозревателе объектов щелкните правой кнопкой мыши имя экземпляра и выберите **монитор активности**.  
  
#### <a name="to-open-activity-monitor-when-opening-sql-server-management-studio"></a>Открытие монитора активности при открытии среды SQL Server Management Studio  
  
1.  В меню **Сервис** выберите команду **Параметры**.  
  
2.  В диалоговом окне **Параметры** последовательно раскройте элементы **Среда**, а затем щелкните **Общие**.  
  
3.  В области **При запуске** выберите **Открыть обозреватель объектов и монитор активности**.  
  
4.  Чтобы изменения вступили в силу, закройте и снова откройте среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
###  <a name="Refresh"></a> Чтобы задать интервал обновления монитора активности  
  
-   Откройте монитор активности.  
  
-   Щелкните правой кнопкой мыши пункт **Обзор**, выберите пункт **Интервал обновления**, а затем — интервал, в котором монитор активности будет получать новые данные экземпляра.  
  
  
