---
title: Изменение IP-адреса для экземпляра отказоустойчивого кластера | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- modifying IP addresses
- failover clustering [SQL Server], IP addresses
- IP addresses [SQL Server]
- clusters [SQL Server], IP addresses
ms.assetid: b685f400-cbfe-4c5d-a070-227a1123dae4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a41d2c04929e9b142ac4c1708bb4fedb21d27f8c
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85062537"
---
# <a name="change-the-ip-address-of-a-failover-cluster-instance"></a>Изменение IP-адреса экземпляра отказоустойчивого кластера
  В этом разделе описывается изменение ресурса IP-адреса в экземпляре отказоустойчивого кластера (FCI) AlwaysOn с помощью оснастки «Диспетчер отказоустойчивости кластеров». Оснастка «Диспетчер отказоустойчивости кластеров» — это приложение управления кластером для службы WSFC.  
  
-   **Перед началом работы:**  [Безопасность](#Security)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
 Перед тем как продолжить, просмотрите следующий подраздел электронной документации по [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] : [Подготовка к установке отказоустойчивого кластера](../install/before-installing-failover-clustering.md).  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Обслуживание или обновление экземпляра FCI должно производиться локальным администратором, имеющим разрешение на вход в систему в качестве службы на всех узлах FCI.  
  
##  <a name="using-the-failover-cluster-manager-snap-in"></a><a name="WSFC"></a> Использование оснастки «Диспетчер отказоустойчивости кластеров»  
 **Изменение ресурса IP-адреса для FCI**  
  
1.  Откройте оснастку «Диспетчер отказоустойчивости кластеров»  
  
2.  Разверните узел **Службы и приложения** , на левой панели щелкните экземпляр FCI.  
  
3.  В правой части панели в категории **Имя сервера** щелкните правой кнопкой мыши экземпляр SQL Server и выберите пункт **Свойства** , чтобы открыть диалоговое окно **Свойства** .  
  
4.  На вкладке **Общие** измените ресурс IP-адреса.  
  
5.  Нажмите кнопку **ОК** , чтобы закрыть диалоговое окно.  
  
6.  На панели справа щелкните правой кнопкой мыши элемент SQL IP Address1 (имя экземпляра отказоустойчивого кластера) и выберите пункт **Перейти в режим "вне сети"**. Состояние SQL IP Address1 (имя экземпляра отказоустойчивого кластера), SQL Network Name (имя экземпляра отказоустойчивого кластера) и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] изменится с «в сети» на «ожидание сети», затем на «вне сети».  
  
7.  На панели справа щелкните правой кнопкой мыши [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]и выберите пункт **Подключить**. Состояние SQL IP Address1 (имя экземпляра отказоустойчивого кластера), SQL Network Name (имя экземпляра отказоустойчивого кластера) и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] изменится с «вне сети» на «ожидание сети», затем на «в сети».  
  
8.  Закройте оснастку «Диспетчер отказоустойчивости кластеров».  
  
  
