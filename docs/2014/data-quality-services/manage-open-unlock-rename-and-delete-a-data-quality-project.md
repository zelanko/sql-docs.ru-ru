---
title: Управление (открытие, разблокировка, переименование и удаление) проекта качества данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.dqproject.opendqproject.f1
helpviewer_keywords:
- data quality project,delete
- data quality project,rename
- data quality project,unlock
- data quality project,open
ms.assetid: de8a2b04-4673-4beb-b4cf-96a28cdf3a93
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: d5e3ec1fc7c3c811b588aaf4145aa286d9aa078e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "65484156"
---
# <a name="manage-open-unlock-rename-and-delete-a-data-quality-project"></a>Управление проектом служб DQS (открытие, разблокировка, переименование и удаление)
  В этом разделе описывается управление проектом служб DQS с помощью [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] : такие действия, как открытие, разблокирование, переименование и удаление проекта.  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> Ограничения  
  
-   Нельзя открыть заблокированный проект, созданный другим пользователем.  
  
-   Невозможно разблокировать, переименовать или удалить проект служб DQS, созданный другим пользователем.  
  
-   Нельзя удалить заблокированный проект служб DQS. Чтобы проект можно было удалить, его необходимо сначала разблокировать.  
  
-   Вы можете разблокировать только тот проект служб DQS, который сами создали.  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Предварительные требования  
 Для управления должен быть в наличии хотя бы один проект служб DQS.  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Для управления проектом служб DQS необходимо иметь роль dqs_kb_editor или dqs_kb_operator в базе данных DQS_MAIN.  
  
##  <a name="open-a-data-quality-project"></a><a name="Open"></a> Открытие проекта служб DQS  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][Запустите приложение Data Quality Client](../../2014/data-quality-services/run-the-data-quality-client-application.md).  
  
2.  На [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] главном экране щелкните **Open Data Quality Project (открыть проект**служб DQS). Появится экран **Открытие проекта** .  
  
     Также вы можете напрямую открыть проект служб DQS, щелкнув его в области **Последние проекты служб DQS** .  
  
3.  На экране **Открытие проекта** щелчком выберите нужный проект служб DQS и нажмите кнопку **Далее**.  
  
4.  Проект служб DQS откроется в том же состоянии, в каком он был закрыт в последний раз. Проект служб DQS имеет следующие состояния:  
  
    -   Для действия **Очистка** проект качества данных может иметь следующие состояния: **Очистка-Map**, **Очистка — Очистка**, **Очистка — управление и просмотр результатов**, а также **Очистка и экспорт**.  
  
    -   Для действия **сопоставления** проект качества данных может иметь следующие состояния: **Match-Map**, **Match-Match**, **Match-выживания**и **Match-Export**.  
  
##  <a name="unlock-a-data-quality-project"></a><a name="Unlock"></a> Разблокирование проекта служб DQS  
 При создании проекта служб DQS он находится в заблокированном состоянии для предотвращения использования или изменения другими пользователями. Необходимо разблокировать проект служб DQS после завершения работы, если требуется, чтобы с этим проектом могли работать другие пользователи. Для заблокированных проектов отображается символ блокировки.  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][Запустите приложение Data Quality Client](../../2014/data-quality-services/run-the-data-quality-client-application.md).  
  
2.  На [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] главном экране щелкните **Open Data Quality Project (открыть проект**служб DQS). Появится экран **Открытие проекта** .  
  
3.  На экране **Открытие проекта** щелкните правой кнопкой мыши созданный вами заблокированный проект служб DQS, затем выберите **Разблокировать** в контекстном меню. Рядом с именем проекта отобразится зеленый флажок, означающий, что проект разблокирован.  
  
##  <a name="rename-a-data-quality-project"></a><a name="Rename"></a> Переименование проекта служб DQS  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][Запустите приложение Data Quality Client](../../2014/data-quality-services/run-the-data-quality-client-application.md).  
  
2.  На [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] главном экране щелкните **Open Data Quality Project (открыть проект**служб DQS). Появится экран **Открытие проекта** .  
  
3.  На экране **Открытие проекта** щелкните правой кнопкой мыши созданный вами проект служб DQS, затем выберите **Переименовать** в контекстном меню.  
  
4.  Имя проекта служб DQS станет доступным для редактирования в столбце **Имя** . Введите новое имя и нажмите клавишу «Ввод».  
  
##  <a name="delete-a-data-quality-project"></a><a name="Delete"></a> Удаление проекта служб DQS  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][Запустите приложение Data Quality Client](../../2014/data-quality-services/run-the-data-quality-client-application.md).  
  
2.  На [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] главном экране щелкните **Open Data Quality Project (открыть проект**служб DQS). Появится экран **Открытие проекта** .  
  
3.  На экране **Открытие проекта** щелкните правой кнопкой мыши созданный вами разблокированный проект служб DQS, затем выберите **Удалить** в контекстном меню.  
  
4.  Появится окно подтверждения. Нажмите кнопку **Да**.  
  
  
