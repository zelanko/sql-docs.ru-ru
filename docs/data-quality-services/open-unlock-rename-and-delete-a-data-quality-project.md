---
title: Открытие, разблокировка, переименование и удаление проекта служб DQS | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: data-quality-services
ms.component: data-quality-services
ms.reviewer: ''
ms.suite: sql
ms.technology:
- data-quality-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.dqs.dqproject.opendqproject.f1
helpviewer_keywords:
- data quality project,delete
- data quality project,rename
- data quality project,unlock
- data quality project,open
ms.assetid: de8a2b04-4673-4beb-b4cf-96a28cdf3a93
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e0c3a8c66481b3c87ea263d4362335cedd452b83
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="open-unlock-rename-and-delete-a-data-quality-project"></a>Открытие, разблокировка, переименование и удаление проекта качества данных

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  В этом разделе описывается управление проектом служб DQS с помощью [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] : такие действия, как открытие, разблокирование, переименование и удаление проекта.  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="LimitationsRestrictions"></a> ограничения  
  
-   Нельзя открыть заблокированный проект, созданный другим пользователем.  
  
-   Невозможно разблокировать, переименовать или удалить проект служб DQS, созданный другим пользователем.  
  
-   Нельзя удалить заблокированный проект служб DQS. Чтобы проект можно было удалить, его необходимо сначала разблокировать.  
  
-   Вы можете разблокировать только тот проект служб DQS, который сами создали.  
  
###  <a name="Prerequisites"></a> Предварительные требования  
 Для управления должен быть в наличии хотя бы один проект служб DQS.  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Для управления проектом служб DQS необходимо иметь роль dqs_kb_editor или dqs_kb_operator в базе данных DQS_MAIN.  
  
##  <a name="Open"></a> Открытие проекта служб DQS  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Запуск клиентского приложения Data Quality Client](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  На главном экране [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] нажмите кнопку **Открыть проект служб DQS**. Появится экран **Открытие проекта** .  
  
     Также вы можете напрямую открыть проект служб DQS, щелкнув его в области **Последние проекты служб DQS** .  
  
3.  На экране **Открытие проекта** щелчком выберите нужный проект служб DQS и нажмите кнопку **Далее**.  
  
4.  Проект служб DQS откроется в том же состоянии, в каком он был закрыт в последний раз. Проект служб DQS имеет следующие состояния:  
  
    -   Для действия **Очистка** проект качества данных может иметь следующие состояния: **Очистка — сопоставить**, **Очистка — очистить**, **Очистка — управление и просмотр результатов**и **Очистка — экспорт**.  
  
    -   Для действия **Сопоставление** проект качества данных может иметь следующие состояния: **Сопоставление — сопоставить**, **Сопоставление — сопоставление**, **Сопоставление — Сохранение**и **Сопоставление — экспорт**.  
  
##  <a name="Unlock"></a> Разблокирование проекта служб DQS  
 При создании проекта служб DQS он находится в заблокированном состоянии для предотвращения использования или изменения другими пользователями. Необходимо разблокировать проект служб DQS после завершения работы, если требуется, чтобы с этим проектом могли работать другие пользователи. Для заблокированных проектов отображается символ блокировки.  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Запуск клиентского приложения Data Quality Client](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  На главном экране [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] нажмите кнопку **Открыть проект служб DQS**. Появится экран **Открытие проекта** .  
  
3.  На экране **Открытие проекта** щелкните правой кнопкой мыши созданный вами заблокированный проект служб DQS, затем выберите **Разблокировать** в контекстном меню. Рядом с именем проекта отобразится зеленый флажок, означающий, что проект разблокирован.  
  
##  <a name="Rename"></a> Переименование проекта служб DQS  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Запуск клиентского приложения Data Quality Client](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  На главном экране [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] нажмите кнопку **Открыть проект служб DQS**. Появится экран **Открытие проекта** .  
  
3.  На экране **Открытие проекта** щелкните правой кнопкой мыши созданный вами проект служб DQS, затем выберите **Переименовать** в контекстном меню.  
  
4.  Имя проекта служб DQS станет доступным для редактирования в столбце **Имя** . Введите новое имя и нажмите клавишу «Ввод».  
  
##  <a name="Delete"></a> Удаление проекта служб DQS  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Запуск клиентского приложения Data Quality Client](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  На главном экране [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] нажмите кнопку **Открыть проект служб DQS**. Появится экран **Открытие проекта** .  
  
3.  На экране **Открытие проекта** щелкните правой кнопкой мыши созданный вами разблокированный проект служб DQS, затем выберите **Удалить** в контекстном меню.  
  
4.  Появится окно подтверждения. Нажмите кнопку **Да**.  
  
  
