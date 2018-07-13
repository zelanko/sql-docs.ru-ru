---
title: Регистрация подключенного сервера (SQL Server Management Studio) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.registerserver.f1
helpviewer_keywords:
- Registered Servers [SQL Server], register connected servers
- connected server registrations [SQL Server]
ms.assetid: 77deb5f5-0f80-484f-8b8b-29afa67ec18f
caps.latest.revision: 21
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f50b659c4b42a644dfd0510769bbfe7047c13595
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37278200"
---
# <a name="register-a-connected-server-sql-server-management-studio"></a>Регистрация подключенного сервера (среда SQL Server Management Studio)
  В этом разделе описано, как производить регистрацию серверов в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Регистрация сервера дает возможность сохранить данные о соединении для тех серверов, к которым часто осуществляется доступ. Сервер может быть зарегистрирован перед установкой соединения или во время соединения из обозревателя объектов.  
  
 **В этом разделе**  
  
-   **Регистрация сервера с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-register-a-connected-server"></a>Регистрация подключенного сервера  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши имя сервера, с которым уже установлено соединение, а затем нажмите кнопку **Зарегистрировать**.  
  
     **Имя сервера**  
     Введите имя сервера, которое нужно использовать для зарегистрированного сервера. Регистрация локального или удаленного сервера с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] позволяет сохранить сведения о соединении с сервером для будущих соединений. Значением по умолчанию для этого поля является имя сервера, введенное при соединении с ним. Можно оставить это имя сервера или ввести другое легко запоминающееся имя.  
  
     **Описание сервера**  
     Введите необязательное описание сервера. Максимально допустимое количество знаков — 250.  
  
     **Выберите группу серверов**  
     Выберите группу серверов, в которой нужно сохранить регистрацию сервера.  
  
     **Создать группу**  
     Щелкните, чтобы открыть диалоговое окно **Создать группу**, в котором нужно создать новую группу серверов для зарегистрированного сервера.  
  
     **Сохранить**  
     Выберите, чтобы сохранить введенные данные и создать зарегистрированный сервер.  
  
  
