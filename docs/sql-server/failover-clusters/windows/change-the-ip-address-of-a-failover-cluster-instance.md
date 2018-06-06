---
title: Изменение IP-адреса для экземпляра отказоустойчивого кластера | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- modifying IP addresses
- failover clustering [SQL Server], IP addresses
- IP addresses [SQL Server]
- clusters [SQL Server], IP addresses
ms.assetid: b685f400-cbfe-4c5d-a070-227a1123dae4
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: db465f53844bc6a737c5b4c57e7c6f2a92e06835
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2018
ms.locfileid: "34772370"
---
# <a name="change-the-ip-address-of-a-failover-cluster-instance"></a>Изменение IP-адреса экземпляра отказоустойчивого кластера
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В этом разделе описывается изменение ресурса IP-адреса в экземпляре отказоустойчивого кластера (FCI) AlwaysOn с помощью оснастки "Диспетчер отказоустойчивости кластеров". Оснастка «Диспетчер отказоустойчивости кластеров» — это приложение управления кластером для службы WSFC.  
  
-   **Before you begin:**  [Security](#Security)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
 Перед тем как продолжить, просмотрите следующий подраздел электронной документации по [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] : [Подготовка к установке отказоустойчивого кластера](../../../sql-server/failover-clusters/install/before-installing-failover-clustering.md).  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Обслуживание или обновление экземпляра FCI должно производиться локальным администратором, имеющим разрешение на вход в систему в качестве службы на всех узлах FCI.  
  
##  <a name="WSFC"></a> Использование оснастки «Диспетчер отказоустойчивости кластеров»  
 **Изменение ресурса IP-адреса для FCI**  
  
1.  Откройте оснастку «Диспетчер отказоустойчивости кластеров»  
  
2.  Разверните узел **Службы и приложения** , на левой панели щелкните экземпляр FCI.  
  
3.  В правой части панели в категории **Имя сервера** щелкните правой кнопкой мыши экземпляр SQL Server и выберите пункт **Свойства** , чтобы открыть диалоговое окно **Свойства** .  
  
4.  На вкладке **Общие** измените ресурс IP-адреса.  
  
5.  Чтобы закрыть диалоговое окно, нажмите кнопку **ОК** .  
  
6.  На панели справа щелкните правой кнопкой мыши элемент SQL IP Address1 (имя экземпляра отказоустойчивого кластера) и выберите пункт **Перейти в режим "вне сети"**. Состояние SQL IP Address1 (имя экземпляра отказоустойчивого кластера), SQL Network Name (имя экземпляра отказоустойчивого кластера) и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] изменится с «в сети» на «ожидание сети», затем на «вне сети».  
  
7.  На панели справа щелкните правой кнопкой мыши [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]и выберите пункт **Подключить**. Состояние SQL IP Address1 (имя экземпляра отказоустойчивого кластера), SQL Network Name (имя экземпляра отказоустойчивого кластера) и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] изменится с «вне сети» на «ожидание сети», затем на «в сети».  
  
8.  Закройте оснастку «Диспетчер отказоустойчивости кластеров».  
  
  
