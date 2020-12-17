---
description: Установка параметров шифрования на целевых серверах
title: Установка параметров шифрования на целевых серверах
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, encryption
- target servers [SQL Server], encryption
- multiserver environments [SQL Server], setting encryption options on target servers
ms.assetid: 1a9fd539-e166-4ea8-9f21-ac400ca74dee
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016
ms.openlocfilehash: 09454c54f5c0f66201df1bf1968b6dfd3aaa2705
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97464355"
---
# <a name="set-encryption-options-on-target-servers"></a>Установка параметров шифрования на целевых серверах
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> В [Управляемом экземпляре Azure SQL](/azure/sql-database/sql-database-managed-instance) в настоящее время поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия в T-SQL между Управляемым экземпляром SQL Azure и SQL Server](/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Если нельзя использовать сертификат для шифрования передаваемых данных по протоколу TLS (прежнее название — SSL) между главными серверами и некоторыми или всеми целевыми серверами, но канал между ними необходимо шифровать, настройте целевой сервер на использование необходимого уровня безопасности.  
  
Чтобы настроить соответствующий уровень безопасности, необходимый для конкретного канала связи главного и целевого серверов, задайте для подраздела реестра **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\** \<*instance_name*> **\SQLServerAgent\MsxEncryptChannelOptions(REG_DWORD)** агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на целевом сервере одно из следующих значений. Значением \<*instance_name*> является **MSSQL.** _n_. Например, **MSSQL.1** или **MSSQL.3**.  
  
|Значение|Описание|  
|---------|---------------|  
|**0**|Отключает шифрование между данным целевым сервером и главным сервером. Выберите этот параметр, только если канал между целевым и главным сервером защищен другими средствами.|  
|**1**|Включает шифрование только между этим целевым сервером и главным сервером, но никакая проверка сертификата не нужна.|  
|**2**|Включает полное шифрование TLS и проверку сертификата между этим целевым сервером и главным сервером. Это значение по умолчанию. Если нет особой причины использовать другое значение, рекомендуется его не изменять.|  
  
Если задано **1** или **2**, необходимо, чтобы шифрование TLS было включено и на главном, и на целевом серверах. Если задано значение **2** , необходимо, чтобы на главном сервере присутствовал сертификат, подписанный должным образом.  
  
> [!CAUTION]  
> [!INCLUDE[ssNoteRegistry](../../includes/ssnoteregistry-md.md)]  
  
## <a name="see-also"></a>См. также:  
[Руководство. включить шифрование соединений в ядре СУБД (диспетчер конфигурации SQL Server)](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)  
