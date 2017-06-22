---
title: "Установка параметров шифрования на целевых серверах | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Agent, encryption
- target servers [SQL Server], encryption
- multiserver environments [SQL Server], setting encryption options on target servers
ms.assetid: 1a9fd539-e166-4ea8-9f21-ac400ca74dee
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 746d0d91d4625c6daad4a4133c0a4481ef85f7d9
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="set-encryption-options-on-target-servers"></a>Установка параметров шифрования на целевых серверах
Если нельзя использовать сертификат для шифрованной связи по протоколу SSL между главными серверами и некоторыми или всеми целевыми серверами, но канал между ними необходимо шифровать, настройте целевой сервер на использование необходимого уровня безопасности.  
  
Чтобы настроить соответствующий уровень безопасности, необходимый для конкретного канала связи главного и целевого серверов, задайте для подраздела реестра **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\**\<*имя_экземпляра*>**\SQLServerAgent\MsxEncryptChannelOptions(REG_DWORD)** агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] на целевом сервере одно из следующих значений: Для параметра \<*имя_экземпляра*> используйте значение **MSSQL.***n*. Например, **MSSQL.1** или **MSSQL.3**.  
  
|Значение|Описание|  
|---------|---------------|  
|**0**|Отключает шифрование между данным целевым сервером и главным сервером. Выберите этот параметр, только если канал между целевым и главным сервером защищен другими средствами.|  
|**1**|Включает шифрование только между этим целевым сервером и главным сервером, но никакая проверка сертификата не нужна.|  
|**2**|Включает полное шифрование SSL и проверку сертификата между этим целевым сервером и главным сервером. Это значение по умолчанию. Если нет особой причины использовать другое значение, рекомендуется его не изменять.|  
  
Если задано **1** или **2** , необходимо, чтобы SSL-шифрование было включено и на главном, и на целевом серверах. Если задано значение **2** , необходимо, чтобы на главном сервере присутствовал сертификат, подписанный должным образом.  
  
> [!CAUTION]  
> [!INCLUDE[ssNoteRegistry](../../includes/ssnoteregistry_md.md)]  
  
## <a name="see-also"></a>См. также:  
[Практическое руководство. Включение шифрования соединений в ядре СУБД (диспетчер конфигурации SQL Server)](http://msdn.microsoft.com/en-us/e1e55519-97ec-4404-81ef-881da3b42006)  
  

