---
title: "Заметки о выпуске SQL Server Management Studio | Документация Майкрософт"
ms.custom: 
ms.date: 06/22/2017
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
ms.translationtype: HT
ms.sourcegitcommit: 223d43974e6b63f7375a3d3e000492612fb6856e
ms.openlocfilehash: 7fb0aa5f5d8b78a4783efdbb4e1f064eb025538a
ms.contentlocale: ru-ru
ms.lasthandoff: 07/31/2017

---
# <a name="sql-server-management-studio----release-notes"></a>Заметки о выпуске SQL Server Management Studio
Добро пожаловать в общедоступную версию SQL Server Management Studio!  Он представляет собой изолированную установку вне выпуска SQL Server. Мы стремимся регулярно обновлять его, добавляя новые возможности, исправления и поддержку новых функций в SQL Server и Базе данных SQL Azure.  
  
Чтобы получить последнюю версию среды SQL Server Management Studio, перейдите на страницу [Скачивание SQL Server Management Studio (службы SSMS)](../ssms/download-sql-server-management-studio-ssms.md).  
  
Ниже перечислены проблемы и ограничения, связанные с последним выпуском SQL Server Management Studio.  

1. **Мастер восстановления баз данных создает неправильный шаблон пути к целевому расположению файла базы данных** Это известная проблема, возникающая, если служба SSMS подключена к серверу под управлением Linux. Несмотря на то, что этот путь выглядит некорректным/ошибочным, он надлежащим образом обрабатывается на стороне сервера, т. е. функциональные проблемы не возникают.

2. **Проблемы с обозревателем файлов**
    - При работе с экземпляром SQL Server 2017 CTP 2.0 для Windows пользовательский интерфейс для браузера файлов в среде SSMS может не открыться, если на сервере установлен пустой гибкий диск или фиксированный диск, защищенный Bitlocker. 
    - Пользовательский интерфейс для браузера файлов больше не поддерживает версии SQL Server 2017 ниже CTP 2.0.
    


3. **Для входа в экземпляр SSMS с помощью универсальной проверки подлинности Active Directory можно использовать только одну учетную запись Azure Active Directory.**  
    Это ограничение распространяется только на универсальную проверку подлинности Active Directory: вы можете входить на разные серверы, используя проверку пароля Active Directory, встроенную проверку подлинности Active Directory и проверку подлинности SQL Server.
    
    Чтобы обойти это ограничение, используйте другой экземпляр среды SSMS для входа в систему с другой учетной записью Azure Active Directory. 
    
4. **Команды платформы приложений уровня данных (DacFx) и конструктор схем в SSMS не поддерживают универсальную проверку подлинности Active Directory.**  
    Команды, использующие DacFx (например, команды импорта и экспорта) и конструктор схем в среде SSMS сейчас не поддерживают универсальную проверку подлинности Active Directory.
    
    Чтобы обойти это ограничение, используйте другие способы проверки подлинности, доступные в SSMS: проверку пароля Active Directory, встроенную проверку подлинности Active Directory и проверку подлинности SQL Server.

5. **Решение SSMS 17.x может подключаться только к экземплярам служб SQL Server 2017 Integrated Services (SSIS 2017).**  
    Мы знаем об ограниченной совместимости служб SQL Server Integration Services, которое не дает подключаться к предыдущим версиям.
    
    Чтобы временно решить эту проблему, подключитесь к экземпляру службы SQL Server Integration Service с помощью [выпуска SSMS, который соответствует вашему экземпляру SSIS](../ssms/previous-sql-server-management-studio-releases.md). 
  
5. **SSMS не сохраняет планы обслуживания для решения SQL Server 2008 R2 и более ранних версий SQL Server.**  
    Мы надеемся устранить это ограничение в будущем. А пока вы сможете сохранять планы обслуживания с помощью выпуска [SSMS 2014](../ssms/previous-sql-server-management-studio-releases.md) .  
    
5. **Для локализованных версий SSMS может потребоваться установка дополнительного пакета безопасности.**  
При использовании локализованных версий SSMS [пакет обновления безопасности KB 2862966](https://support.microsoft.com/en-us/kb/2862966) требуется при установке на следующих платформах: Windows 8, Windows 7, Windows Server 2012 и Windows Server 2008 R2.

5. **При нажатии кнопки "Справка" или клавиши F1 справка не открывается**  
При нажатии кнопки "Справка" или клавиши F1 в некоторых средах отображается следующее сообщение: **Требуется новое приложение для открытия ms-xhelp**. Эта ошибка является известной проблемой и будет устранена в будущей версии.
  
## <a name="feedback"></a>Отзывы  
  
![needhelp_person_icon](../ssms/media/needhelp_person_icon.png) [форум клиентских средств SQL](https://social.msdn.microsoft.com/Forums/en-US/home?forum=sqltools) |  [Опубликуйте информацию о проблеме или предложение на Microsoft Connect](https://connect.microsoft.com/SQLServer/Feedback).  
  
## <a name="see-also"></a>См. также:  
[Учебник по среде SQL Server Management Studio](../ssms/use-sql-server-management-studio.md)  
[Скачивание SQL Server Management Studio (службы SSMS)](../ssms/download-sql-server-management-studio-ssms.md)  
[Предыдущие выпуски SQL Server Management Studio](../ssms/previous-sql-server-management-studio-releases.md)  

  

