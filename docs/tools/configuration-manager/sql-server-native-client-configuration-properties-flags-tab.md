---
title: Свойства конфигурации SQL Server Native Client (вкладка "Флаги") | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 59af121d-c8b9-4faa-91a1-b664f2c9b441
author: markingmyname
ms.author: maghan
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: e185c6bd783ef656871ae75e34be3b6a5216964a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68023998"
---
# <a name="sql-server-native-client-configuration-properties-flags-tab"></a>Свойства конфигурации собственного клиента SQL Server (вкладка «Флаги»)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на этом компьютере связываются с серверами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при помощи протоколов, предоставляемых библиотечным файлом собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . На этой странице можно настроить компьютер клиента на запрос зашифрованного соединения на основе протокола SSL. Если не удается установить зашифрованное соединение, подключение завершится с ошибкой.  
  
 Процесс входа в систему всегда шифруется. Указанные далее параметры применимы только к шифрованию данных. Дополнительные сведения о том, как [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняет шифрование обмена данными, а также инструкции по настройке клиента на доверие к корневому центру сертификата сервера см. в статьях о шифровании подключений к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и включении зашифрованных соединений с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)] (диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]) в электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="options"></a>Параметры  
 **Принудительное шифрование протокола**  
 Запрос соединения с использованием SSL.  
  
 **Надежный сертификат сервера**  
 При установке значения **Нет**клиентский процесс выполняет попытку проверки сертификата сервера. И клиент, и сервер должны обладать сертификатами, выданными общим центром сертификации. Если на компьютере клиента нет сертификата или если проверка сертификата заканчивается неудачей, соединение закрывается.  
  
 При установке значения **Да**клиент не проверяет сертификат сервера, тем самым позволяя использовать самозаверяющий сертификат.  
  
 Флаг**Доверять сертификату сервера** используется, только если флаг **Принудительное шифрование протокола** имеет значение **Да**.  
  
  
