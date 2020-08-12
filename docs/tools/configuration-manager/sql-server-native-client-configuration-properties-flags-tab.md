---
title: Свойства конфигурации собственного клиента SQL Server (вкладка «Флаги»)
description: Сведения о параметрах на вкладке "Флаги" диалогового окна "Свойства конфигурации SQL Server Native Client".
ms.custom: seo-lt-2019
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
ms.openlocfilehash: 84cdb363a7cae73f189a22298767e6eb47ef4e54
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85880335"
---
# <a name="sql-server-native-client-configuration-properties-flags-tab"></a>Свойства конфигурации собственного клиента SQL Server (вкладка «Флаги»)
[!INCLUDE [SQL Server Windows Only - ASDBMI ](../../includes/applies-to-version/sql-windows-only-asdbmi.md)]
  Клиенты [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на этом компьютере связываются с серверами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при помощи протоколов, предоставляемых файлом библиотеки нативного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. На этой странице можно настроить компьютер клиента на запрос зашифрованного соединения на основе протокола TLS, заменившем SSL. Если не удается установить зашифрованное соединение, подключение завершится с ошибкой.  
  
 Процесс входа в систему всегда шифруется. Указанные далее параметры применимы только к шифрованию данных. Дополнительные сведения о том, как [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняет шифрование обмена данными, а также инструкции по настройке клиента на доверие к корневому центру сертификата сервера см. в разделах о шифровании соединений с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и статье о том, как включить зашифрованные соединения с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)] (диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])" электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="options"></a>Параметры  
 **Принудительное шифрование протокола**  
 Запрос соединения с использованием TLS.  
  
 **Надежный сертификат сервера**  
 При установке значения **Нет**клиентский процесс выполняет попытку проверки сертификата сервера. И клиент, и сервер должны обладать сертификатами, выданными общим центром сертификации. Если на компьютере клиента нет сертификата или если проверка сертификата заканчивается неудачей, соединение закрывается.  
  
 При установке значения **Да**клиент не проверяет сертификат сервера, тем самым позволяя использовать самозаверяющий сертификат.  
  
 Флаг**Доверять сертификату сервера** используется, только если флаг **Принудительное шифрование протокола** имеет значение **Да**.  
  
  
