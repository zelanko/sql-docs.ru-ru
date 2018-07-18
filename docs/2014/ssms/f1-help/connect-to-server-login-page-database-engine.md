---
title: Подключение к серверу (страница входа) для ядра СУБД | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.connecttosqlserver.login.f1
ms.assetid: e08cfbc3-bed5-4401-a13b-1c66d902fe32
caps.latest.revision: 31
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b7f8c761a052bc3c82789087bb955c760e9a1b49
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37181241"
---
# <a name="connect-to-server-login-page-database-engine"></a>Соединение с сервером (страница "Вход") ядра СУБД
  Используйте эту вкладку для просмотра или задания параметров при соединении с [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
> [!NOTE]  
>  Для подключения с проверкой подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должен быть сконфигурирован в режиме проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и Windows. Дополнительные сведения о том, как определить режим проверки подлинности и режим проверки подлинности, см. в разделе [изменение режима проверки подлинности сервера](../../database-engine/configure-windows/change-server-authentication-mode.md).  
  
## <a name="options"></a>Параметры  
 **Тип сервера**  
 При регистрации сервера из обозревателя объектов выберите тип сервера для подключения: [!INCLUDE[ssDE](../../includes/ssde-md.md)], службы Analysis Services, службы Reporting Services или службы Integration Services. В остальной части диалогового окна показаны параметры, которые применяются только к выбранному типу сервера. При регистрации сервера c панели "Зарегистрированные серверы" поле **Тип сервера** не может быть изменено и совпадает с типом сервера, показанного в компоненте "Зарегистрированные серверы". Чтобы зарегистрировать другой тип сервера, выберите компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)], службы Analysis Services, службы Reporting Services или службы Integration Services на панели инструментов «Зарегистрированные серверы», прежде чем начать регистрацию нового сервера.  
  
 При соединении с экземпляром ядра СУБД [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] через [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]необходимо использовать проверку подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и указать базу данных в диалоговом окне **Соединение с сервером** на вкладке **Свойства соединения** . Обязательно установите флажок **Шифрование соединения** .  
  
 По умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] соединяется с базой данных **master**. Если указать пользовательскую базу данных, то в обозревателе объектов будет видна только эта база данных и ее объекты. Если соединиться с базой данных **master**, будут видны все базы данных. Дополнительные сведения см. в разделе [Общие сведения о базе данных SQL Windows Azure](http://go.microsoft.com/fwlink/?LinkId=163948).  
  
 **Имя сервера**  
 Выберите экземпляр сервера для подключения. По умолчанию выводится экземпляр сервера, к которому подключение выполнялось в последний раз.  
  
 **Проверка подлинности**  
 При соединении с экземпляром [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]доступны два режима проверки подлинности.  
  
 При соединении с экземпляром ядра СУБД [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] через [!INCLUDE[ssSDS](../../includes/sssds-md.md)]необходимо использовать проверку подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и указать базу данных в диалоговом окне **Соединение с сервером** на вкладке **Свойства соединения** . Обязательно установите флажок **Шифрование соединения** .  
  
 По умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] соединяется с базой данных **master**. Если указать пользовательскую базу данных, то в обозревателе объектов будет видна только эта база данных и ее объекты. Если соединиться с базой данных **master**, будут видны все базы данных. Дополнительные сведения см. в разделе [Общие сведения о базе данных SQL Windows Azure](http://go.microsoft.com/fwlink/?LinkId=163948).  
  
 **Режим проверки подлинности Windows (проверка подлинности Windows)**  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Режим проверки подлинности Windows позволяет подключаться с учетной записью Windows.  
  
 **Проверка подлинности SQL Server**  
 При подключении пользователя с указанным именем входа и паролем не через доверенное соединение [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняет проверку подлинности самостоятельно по наличию учетной записи входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и совпадения указанного пароля с ранее сохраненным. Если в службе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не задана учетная запись входа, проверка подлинности завершается ошибкой, о которой пользователь получит сообщение.  
  
> [!IMPORTANT]  
>  По возможности используйте аутентификацию Windows.  
  
 **Имя пользователя**  
 Введите имя пользователя для соединения. Этот параметр доступен только при соединении с использованием метода проверки подлинности Windows.  
  
 **Имя входа**  
 Введите имя входа для подключения. Этот параметр доступен только в том случае, если выбрано соединение с использованием проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Пароль**  
 Введите пароль для этого имени входа. Этот параметр доступен для редактирования только при подключении с проверкой подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Запомнить пароль**  
 Выберите, чтобы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сохранил введенный пароль. Этот параметр отображается только в том случае, если выбрано подключение с проверкой подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Connect**  
 Нажмите, чтобы подключиться к выбранному выше серверу.  
  
 **Параметры**  
 Нажмите, чтобы изменить вид диалогового окна и скрыть дополнительные параметры соединения с сервером (такие как «Запомнить пароль»).  
  
  
