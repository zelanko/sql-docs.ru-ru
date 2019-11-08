---
title: Использование поставщика WMI для управления конфигурацией
ms.custom: seo-lt-2019
ms.date: 04/12/2019
ms.prod: sql
ms.prod_service: database-engine
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
ms.openlocfilehash: d76cc006e2f8638de9b6d3c21660806239022ec0
ms.sourcegitcommit: baa40306cada09e480b4c5ddb44ee8524307a2ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/06/2019
ms.locfileid: "73657378"
---
# <a name="working-with-the-wmi-provider-for-configuration-management"></a>Работа с поставщиком WMI для управления конфигурацией

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

В этой статье приводятся рекомендации по программированию с помощью поставщика WMI для управления компьютером.

## <a name="binding"></a>Binding  
 Поставщик WMI для управления компьютером является моделью объектов COM, он поддерживает раннее и позднее связывания. В случае позднего связывания при помощи таких языков скриптов, как VBScript, можно программно управлять службами, параметрами сети и псевдонимами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="specifying-a-connection-string"></a>Задание строки соединения

Приложения направляют поставщика WMI для управления конфигурацией к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] путем соединения с пространством имен WMI, определенным поставщиком. Служба WMI Windows сопоставляет это пространство имен с библиотекой DLL поставщика и загружает библиотеку DLL в память. Все экземпляры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] представлены одним пространством имен WMI.

Пространство имен по умолчанию имеет следующий формат. В формате `VV` — основной номер версии SQL Server. Это число можно обнаружить, запустив `SELECT @@VERSION;`.

```console
\\.\root\Microsoft\SqlServer\ComputerManagementVV
```

При подключении с помощью PowerShell необходимо удалить начальный `\\.\`. Например, следующий код PowerShell перечисляет все классы WMI для SQL Server 2016, которая является основной версией 13.

```powershell
Get-WmiObject -Namespace 'root\Microsoft\SqlServer\ComputerManagement13' -List
```

<!--
Updated this on 2019-04-12, per:
   ~ https://github.com/MicrosoftDocs/sql-docs/issues/1817
   ~ https://github.com/rrg92/sql-docs/commit/3d518bfc0d55f819c762abc3e5c5c9eed85abe94?diff=unified

Thus from here I (GeneMi = MightyPen) removed the following text about 'instance_name':

'root\Microsoft\SqlServer\ComputerManagement13\instance_name'

where `instance_name` defaults to `MSSQLSERVER` in a default installation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
-->

Для запроса всех доступных пространств имен WMI Компутерманажемент можно использовать следующий код PowerShell.

```powershell
gwmi -ns 'root\Microsoft\SqlServer' __NAMESPACE | ? {$_.name -match 'ComputerManagement' } | select name
```

 **Примечание.** При подключении через брандмауэр Windows необходимо убедиться, что компьютеры настроены соответствующим образом. См. статью "подключение через брандмауэр Windows" в документации инструментарий управления Windows (WMI) на [веб-сайте](https://go.microsoft.com/fwlink/?linkid=15426)[!INCLUDE[msCoName](../../includes/msconame-md.md)] MSDN.  
  
## <a name="permissions-and-server-authentication"></a>Разрешения и проверка подлинности сервера  
 Чтобы получить доступ к поставщику WMI для управления конфигурацией, скрипт управления WMI клиента должен выполняться на целевом компьютере в контексте администратора. Необходимо членство в локальной группе администраторов Windows на компьютере, которым требуется управлять.  
  
 Администратор может задавать групповые политики для управления доступом пользователей к поставщикам WMI. Дополнительные сведения о задании групповых политик см. в разделе «Групповая политика и MMC» в справке по диспетчеру конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 При помощи скрипта управления инструментарием WMI можно обновлять учетную запись, под которой выполняются службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Поставщик WMI для управления конфигурацией поддерживает сертификаты безопасности. Дополнительные сведения о сертификатах см. в разделе [Иерархия шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md).  
  
## <a name="see-also"></a>См. также раздел  
 [Диспетчер конфигурации SQL Server](../../relational-databases/sql-server-configuration-manager.md)  
  
  
