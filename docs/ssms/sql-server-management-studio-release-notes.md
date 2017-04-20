---
title: "Заметки о выпуске SQL Server Management Studio | Документация Майкрософт"
ms.custom: 
ms.date: 01/30/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b95337b-80bf-4624-8f5d-cdaf6181d3b8
caps.latest.revision: 51
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 51e336a22d0c1052c48b8e569330aef26f2af094
ms.lasthandoff: 04/11/2017

---
# <a name="sql-server-management-studio----release-notes"></a>Заметки о выпуске SQL Server Management Studio
Добро пожаловать в общедоступную версию SQL Server Management Studio!  Он представляет собой изолированную установку вне выпуска SQL Server. Мы стремимся регулярно обновлять его, добавляя новые возможности, исправления и поддержку новых функций в SQL Server и Базе данных SQL Azure.  
  
Чтобы получить последнюю версию среды SQL Server Management Studio, перейдите на страницу [Download SQL Server Management Studio &#40;SSMS&#41;](../ssms/download-sql-server-management-studio-ssms.md).  
  
Ниже перечислены проблемы и ограничения, связанные с последним выпуском SQL Server Management Studio.  

1. **Для входа в экземпляр SSMS с помощью универсальной проверки подлинности Active Directory можно использовать только одну учетную запись Azure Active Directory.**  
    Это ограничение распространяется только на универсальную проверку подлинности Active Directory: вы можете входить на разные серверы, используя проверку пароля Active Directory, встроенную проверку подлинности Active Directory и проверку подлинности SQL Server.
    
    Чтобы обойти это ограничение, используйте другой экземпляр среды SSMS для входа в систему с другой учетной записью Azure Active Directory. 
    
2. **Команды платформы приложений уровня данных (DacFx) и конструктор схем в SSMS не поддерживают универсальную проверку подлинности Active Directory.**  
    Команды, использующие DacFx (например, команды импорта и экспорта) и конструктор схем в среде SSMS сейчас не поддерживают универсальную проверку подлинности Active Directory.
    
    Чтобы обойти это ограничение, используйте другие способы проверки подлинности, доступные в SSMS: проверку пароля Active Directory, встроенную проверку подлинности Active Directory и проверку подлинности SQL Server.

3. **Решение SSMS может подключаться только к экземплярам служб SQL Server 2016 Integrated Services (SSIS 2016).**  
    Мы знаем об ограниченной совместимости служб SQL Server Integration Services, которое не дает подключаться к предыдущим версиям.
    
    Чтобы временно решить эту проблему, подключитесь к экземпляру службы SQL Server Integration Service с помощью [выпуска SSMS, который соответствует вашему экземпляру SSIS](../ssms/previous-sql-server-management-studio-releases.md). 
  
4. **SSMS не сохраняет планы обслуживания для решения SQL Server 2008 R2 и более ранних версий SQL Server.**  
    Мы надеемся устранить это ограничение в будущем. А пока вы сможете сохранять планы обслуживания с помощью выпуска [SSMS 2014](../ssms/previous-sql-server-management-studio-releases.md) .  
    
5. **Для локализованных версий SSMS может потребоваться установка дополнительного пакета безопасности.**  
При использовании локализованных версий SSMS [пакет обновления безопасности KB 2862966](https://support.microsoft.com/en-us/kb/2862966) требуется при установке на следующих платформах: Windows 8, Windows 7, Windows Server 2012 и Windows Server 2008 R2.
  
6. **Диспетчер конфигурации SQL Server не будет запущен, если на клиентском компьютере не установлено решение SQL Server.**  
    Если на клиентском компьютере не установлено решение SQL Server, а вы запускаете диспетчер конфигурации SQL Server, появится следующее сообщение об ошибке:   
     `Cannot connect to WMI provider. You do not have permission or the server is unreachable. Note that you can only manage SQL Server 2005 and later servers with SQL Server Configuration Manager. Invalid namespace \[0x8004100e]`,   
   
     * Если экземпляр SQL Server добавлен в список зарегистрированных серверов в среде SSMS:  
        1. Перейдите в представление "Зарегистрированные серверы" в среде SSMS.  
        2. Щелкните правой кнопкой мыши экземпляр SQL Server, который нужно настроить.  
        3. Запустите диспетчер конфигурации SQL Server из контекстного меню.    
          
      * Если экземпляр SQL Server не был добавлен в список зарегистрированных серверов в среде SSMS:  
        1. Откройте командную строку с правами администратора.  
        2. Запустите средство Mofcomp с помощью такой команды:  
    `mofcomp "%programfiles(x86)%\Microsoft SQL Server\130\Shared\sqlmgmproviderxpsp2up.mof"`  
        3. Чтобы после запуска средства Mofcomp изменения вступили в силу, перезапустите службу WMI с помощью такой команды:  
        `net stop "Windows Management Instrumentation"`  
        `net start “Windows Management Instrumentation”`  

## <a name="feedback"></a>Отзывы  
  
![needhelp_person_icon](../ssms/media/needhelp_person_icon.png) [форум клиентских средств SQL](https://social.msdn.microsoft.com/Forums/en-US/home?forum=sqltools) |  [Опубликуйте информацию о проблеме или предложение на Microsoft Connect](https://connect.microsoft.com/SQLServer/Feedback).  
  
## <a name="see-also"></a>См. также:  
[Учебник по среде SQL Server Management Studio](../ssms/use-sql-server-management-studio.md)  
[Скачивание SQL Server Management Studio (службы SSMS)](../ssms/download-sql-server-management-studio-ssms.md)  
[Предыдущие выпуски SQL Server Management Studio](../ssms/previous-sql-server-management-studio-releases.md)  

  

