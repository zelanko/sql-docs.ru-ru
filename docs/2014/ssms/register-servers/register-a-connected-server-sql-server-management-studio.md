---
title: Регистрация подключенного сервера
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.registerserver.f1
helpviewer_keywords:
- Registered Servers [SQL Server], register connected servers
- connected server registrations [SQL Server]
ms.assetid: 77deb5f5-0f80-484f-8b8b-29afa67ec18f
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 93fcd53b0abbbae6855d32cd215327ebfafe9889
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "84994765"
---
# <a name="register-a-connected-server-sql-server-management-studio"></a>Регистрация подключенного сервера (среда SQL Server Management Studio)
  В этом разделе описано, как производить регистрацию серверов в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Регистрация сервера дает возможность сохранить данные о соединении для тех серверов, к которым часто осуществляется доступ. Сервер может быть зарегистрирован перед установкой соединения или во время соединения из обозревателя объектов.  
  
 **В этом разделе**  
  
-   **Регистрация сервера с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-register-a-connected-server"></a>Регистрация подключенного сервера  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши имя сервера, с которым уже установлено соединение, а затем нажмите кнопку **Зарегистрировать**.  
  
     **Имя сервера**  
     Введите имя сервера, которое нужно использовать для зарегистрированного сервера. Регистрация локального или удаленного сервера с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] позволяет сохранить сведения о соединении с сервером для будущих соединений. Значением по умолчанию для этого поля является имя сервера, введенное при соединении с ним. Можно оставить это имя сервера или ввести другое легко запоминающееся имя.  
  
     **Описание сервера**  
     Введите необязательное описание сервера. Максимально допустимое количество знаков — 250.  
  
     **Выберите группу серверов**  
     Выберите группу серверов, в которой нужно сохранить регистрацию сервера.  
  
     **Новая группа**  
     Щелкните, чтобы открыть диалоговое окно **Создать группу**, в котором нужно создать новую группу серверов для зарегистрированного сервера.  
  
     **Сохранить**  
     Выберите, чтобы сохранить введенные данные и создать зарегистрированный сервер.  
  
  
