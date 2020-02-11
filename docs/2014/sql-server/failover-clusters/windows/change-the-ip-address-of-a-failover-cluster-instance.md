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
manager: craigg
ms.openlocfilehash: 9a9a93c9c6efdd5a864b5ab3ce0beacb7cbf1632
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63049631"
---
# <a name="change-the-ip-address-of-a-failover-cluster-instance"></a>Изменение IP-адреса экземпляра отказоустойчивого кластера
  В этом разделе описывается изменение ресурса IP-адреса в экземпляре отказоустойчивого кластера (FCI) AlwaysOn с помощью оснастки «Диспетчер отказоустойчивости кластеров». Оснастка «Диспетчер отказоустойчивости кластеров» — это приложение управления кластером для службы WSFC.  
  
-   **Перед началом:**  [Безопасность](#Security)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
 Перед тем как продолжить, просмотрите следующий подраздел электронной документации по [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] : [Подготовка к установке отказоустойчивого кластера](../install/before-installing-failover-clustering.md).  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Обслуживание или обновление экземпляра FCI должно производиться локальным администратором, имеющим разрешение на вход в систему в качестве службы на всех узлах FCI.  
  
##  <a name="WSFC"></a>Использование оснастки «диспетчер отказоустойчивости кластеров»  
 **Изменение ресурса IP-адреса для FCI**  
  
1.  Откройте оснастку «Диспетчер отказоустойчивости кластеров»  
  
2.  Разверните узел **Службы и приложения** , на левой панели щелкните экземпляр FCI.  
  
3.  В правой части панели в категории **Имя сервера** щелкните правой кнопкой мыши экземпляр SQL Server и выберите пункт **Свойства** , чтобы открыть диалоговое окно **Свойства** .  
  
4.  На вкладке **Общие** измените ресурс IP-адреса.  
  
5.  Нажмите кнопку **ОК**, чтобы закрыть диалоговое окно.  
  
6.  На панели справа щелкните правой кнопкой мыши элемент SQL IP Address1 (имя экземпляра отказоустойчивого кластера) и выберите пункт **Перейти в режим "вне сети"**. Состояние SQL IP Address1 (имя экземпляра отказоустойчивого кластера), SQL Network Name (имя экземпляра отказоустойчивого кластера) и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] изменится с «в сети» на «ожидание сети», затем на «вне сети».  
  
7.  На панели справа щелкните правой кнопкой мыши [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]и выберите пункт **Подключить**. Состояние SQL IP Address1 (имя экземпляра отказоустойчивого кластера), SQL Network Name (имя экземпляра отказоустойчивого кластера) и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] изменится с «вне сети» на «ожидание сети», затем на «в сети».  
  
8.  Закройте оснастку «Диспетчер отказоустойчивости кластеров».  
  
  
