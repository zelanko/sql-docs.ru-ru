---
title: Работа с поставщиком WMI для управления конфигурацией | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- permissions [WMI]
- connection strings [WMI]
- security [WMI]
- WMI Provider for Configuration Management, connection strings
- WMI Provider for Configuration Management, security
- late binding [WMI]
- WMI Provider for Configuration Management, late binding
- binding [WMI]
ms.assetid: 34daa922-7074-41d0-9077-042bb18c222a
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 9d9f3ab9f80c6f2c77153439cf554f0ae8598586
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "68195776"
---
# <a name="working-with-the-wmi-provider-for-configuration-management"></a>Работа с поставщиком WMI для управления конфигурацией
  Перед тем как приступить к программированию с помощью поставщика WMI для управления компьютером, примите во внимание следующие сведения.  
  
## <a name="binding"></a>Привязка  
 Поставщик WMI для управления компьютером является моделью объектов COM, он поддерживает раннее и позднее связывания. В случае позднего связывания при помощи таких языков скриптов, как VBScript, можно программно управлять службами, параметрами сети и псевдонимами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Дополнительные сведения о программировании поставщиков WMI с помощью языков сценариев см. на [!INCLUDE[msCoName](../../includes/msconame-md.md)] [веб-сайте](https://go.microsoft.com/fwlink/?linkid=15426)MSDN.  
  
## <a name="specifying-a-connection-string"></a>Задание строки соединения  
 Приложения направляют поставщика WMI для управления конфигурацией к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] путем соединения с пространством имен WMI, определенным поставщиком. Служба Windows WMI сопоставляет это пространство имен с файлом DLL поставщика и загружает его в память. Все экземпляры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] представлены одним пространством имен WMI. Значение по умолчанию этого пространства имен:  
  
```  
\\.\root\Microsoft\SqlServer\ComputerManagement12\instance_name  
```  
  
 где `instance_name` в установке по умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имеет значение по умолчанию `MSSQLSERVER`.  
  
 **Примечание.** При подключении через брандмауэр Windows необходимо убедиться, что компьютеры настроены соответствующим образом. См. статью "подключение через брандмауэр Windows" в документации инструментарий управления Windows (WMI) на [!INCLUDE[msCoName](../../includes/msconame-md.md)] [веб-сайте](https://go.microsoft.com/fwlink/?linkid=15426)MSDN.  
  
## <a name="permissions-and-server-authentication"></a>Разрешения и проверка подлинности сервера  
 Чтобы получить доступ к поставщику WMI для управления конфигурацией, скрипт управления WMI клиента должен выполняться на целевом компьютере в контексте администратора. Необходимо членство в локальной группе администраторов Windows на компьютере, которым требуется управлять.  
  
 Администратор может задавать групповые политики для управления доступом пользователей к поставщикам WMI. Дополнительные сведения о задании групповых политик см. в разделе «Групповая политика и MMC» в справке по диспетчеру конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 При помощи скрипта управления инструментарием WMI можно обновлять учетную запись, под которой выполняются службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Поставщик WMI для управления конфигурацией поддерживает сертификаты безопасности. Дополнительные сведения о сертификатах см. в разделе [Иерархия шифрования](../security/encryption/encryption-hierarchy.md).  
  
## <a name="see-also"></a>См. также  
 [Диспетчер конфигурации SQL Server](../sql-server-configuration-manager.md)  
  
  
