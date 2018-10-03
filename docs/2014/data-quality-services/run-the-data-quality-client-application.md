---
title: Запуск клиентского приложения Data Quality Client | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.browseforservers.f1
- sql12.dqs.connecttoserver.f1
ms.assetid: 0b2aa202-7ab2-4c9d-b0f1-802588053a1e
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 74968a185a5b9e3d0ff4dfe1da7dcbb374bfdc4b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48140574"
---
# <a name="run-the-data-quality-client-application"></a>Запуск клиентского приложения DQS
  Чтобы использовать [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS), следует запустить клиент [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] и войти на сервер [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)].  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Prerequisites"></a> Предварительные требования  
 Необходимо, чтобы установка сервера [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] , запускаемая с помощью файла DQSInstaller.exe, была завершена. Дополнительные сведения см. в разделе [Запуск файла DQSInstaller.exe для завершения установки сервера служб DQS](install-windows/run-dqsinstaller-exe-to-complete-data-quality-server-installation.md).  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Для входа на сервер [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]необходимо иметь одну из трех ролей DQS (dqs_adminstrator, dqs_kb_editor или dqs_kb_operator) в базе данных DQS_MAIN.  
  
##  <a name="Run"></a> Запуск клиента DQS  
 Чтобы запустить клиент [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] на компьютере, где он установлен, выполните следующие действия.  
  
1.  Нажмите кнопку **Пуск**, выберите **Все программы**, затем **[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]**, затем **Службы Data Quality Services**, затем **Data Quality Client**.  
  
2.  В диалоговом окне **Соединение с сервером** выполните следующие действия:  
  
    1.  Укажите сервер, к которому требуется подключить приложение [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] . Выберите **(LOCAL)** для подключения к [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] на локальном компьютере. Вы также можете щелкнуть стрелку и выбрать элемент **\<Поиск дополнительных серверов в сети>**, чтобы подключиться к другому серверу (или подключиться к локальному серверу по имени). Открывается диалоговое окно **Обзор серверов** . Вы можете выбрать сервер на вкладках **Локальные серверы** или **Сетевые серверы** .  
  
    2.  Чтобы зашифровать передачу данных между сервером [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] и клиентом [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)], щелкните **Параметры**, а затем установите флажок **Шифровать соединение**.  
  
3.  Нажмите кнопку **Соединить**.  
  
 Открывается на главном экране клиента [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] . Дополнительные сведения см. в статье [Главный экран клиента DQS](../../2014/data-quality-services/data-quality-client-home-screen.md).  
  
  
