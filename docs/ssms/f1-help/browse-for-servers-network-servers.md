---
title: "Обзор серверов (сетевые серверы) | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.browseservers.network.f1
ms.assetid: a59ffcd6-4b69-4c5c-9740-699ccb2183fb
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 0dfaef0364cf72e994b0fe5de778adc8a18bd715
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="browse-for-servers-network-servers"></a>Обзор серверов (сетевые серверы)
Если при подключении к компоненту [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] неизвестно точное имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], в поле **Имя сервера** нажмите кнопку **Продолжить обзор**, чтобы открыть диалоговое окно **Выбор серверов**.  
  
Это диалоговое окно заполняется службой « [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] , браузер» на серверах. Название экземпляра может не появиться в списке по нескольким причинам, перечисленным ниже.  
  
-   Служба « [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] , браузер» может не работать на компьютере с запущенным [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
-   Возможно, порт UDP 1434 заблокирован брандмауэром.  
  
-   Возможно, установлен флаг **HideInstance** .  
  
Чтобы подключиться к экземпляру, который не появился в списке, введите полную строку соединения для экземпляра, включая номер порта TCP/IP или имя канала именованных каналов.  
  
## <a name="options"></a>Параметры  
**Выберите экземпляр SQL Server в сети для соединения**  
Укажите сервер, с которым нужно соединиться, выбрав экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] , показанный в дереве. Можно показывать или скрывать участки дерева, щелкнув узел, помеченный знаком **+** или **–** .  
  

