---
title: Установка параметров шифрования на целевых серверах | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, encryption
- target servers [SQL Server], encryption
- multiserver environments [SQL Server], setting encryption options on target servers
ms.assetid: 1a9fd539-e166-4ea8-9f21-ac400ca74dee
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b27dd81df572e289d182fdaa637a3af972b3d603
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63244978"
---
# <a name="set-encryption-options-on-target-servers"></a>Установка параметров шифрования на целевых серверах
  Если нельзя использовать сертификат для шифрованной связи по протоколу SSL между главными серверами и некоторыми или всеми целевыми серверами, но канал между ними необходимо шифровать, настройте целевой сервер на использование необходимого уровня безопасности.  
  
 Чтобы настроить соответствующий уровень безопасности, необходимый для конкретного канала связи главного сервера или целевого сервера, задайте для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подраздела реестра агента **\ HKEY_LOCAL_MACHINE \софтваре\микрософт\микрософт SQL Server\\***instance_name*>**\SQLServerAgent\MsxEncryptChannelOptions(REG_DWORD)** \<instance_name \склсерверажент\мсксенкриптчаннелоптионс (REG_DWORD) на целевом сервере одно из следующих значений. Для параметра \<*имя_экземпляра*> используйте значение **MSSQL.**_n_. Например, **MSSQL.1** или **MSSQL.3**.  
  
|Применение|Описание|  
|-----------|-----------------|  
|**0**|Отключает шифрование между данным целевым сервером и главным сервером. Выберите этот параметр, только если канал между целевым и главным сервером защищен другими средствами.|  
|**1**|Включает шифрование только между этим целевым сервером и главным сервером, но никакая проверка сертификата не нужна.|  
|**2**|Включает полное шифрование SSL и проверку сертификата между этим целевым сервером и главным сервером. Это значение по умолчанию. Если нет особой причины использовать другое значение, рекомендуется его не изменять.|  
  
 Если задано **1** или **2** , необходимо, чтобы SSL-шифрование было включено и на главном, и на целевом серверах. Если задано значение **2** , необходимо, чтобы на главном сервере присутствовал сертификат, подписанный должным образом.  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../includes/ssnoteregistry-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Включение шифрования соединений в ядре СУБД (диспетчер конфигурации SQL Server)](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)  
  
  
