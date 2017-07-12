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
ms.translationtype: Human Translation
ms.sourcegitcommit: fe6de2b16b9792a5399b1c014af72a2a5ee52377
ms.openlocfilehash: f593303a681e2f52161777fc48f0fb1b479d20d9
ms.contentlocale: ru-ru
ms.lasthandoff: 06/23/2017

---
<a id="sql-server-management-studio----release-notes" class="xliff"></a>

# Заметки о выпуске SQL Server Management Studio
Добро пожаловать в общедоступную версию SQL Server Management Studio!  Он представляет собой изолированную установку вне выпуска SQL Server. Мы стремимся регулярно обновлять его, добавляя новые возможности, исправления и поддержку новых функций в SQL Server и Базе данных SQL Azure.  
  
Чтобы получить последнюю версию среды SQL Server Management Studio, перейдите на страницу [Download SQL Server Management Studio &#40;SSMS&#41;](../ssms/download-sql-server-management-studio-ssms.md).  
  
Ниже перечислены проблемы и ограничения, связанные с последним выпуском SQL Server Management Studio.  

1. **Мастер восстановления базы данных приводит к возникновению ошибки неправильный шаблон путь к местоположению файла базы данных назначения** 
    Это известная проблема, когда среда SSMS подключена к сервера под управлением Linux. Несмотря на то, что этот путь выглядит неверные или нечетным, правильной обработки на стороне сервера, т. е. нет функционального проблем.

2. **Обозреватель файлов**
    - При работе с экземпляром Windows под управлением SQL Server 2017 г CTP 2.0 браузер файла пользовательского интерфейса в среде SSMS не удается открыть если пустой дисковода гибких дисков или фиксированный диск защищен Bitlocker, которые установлены на сервере. 
    - Интерфейс браузера файл больше не поддерживает версии SQL Server 2017 г. до CTP-версии 2.0.
    


3. **Для входа в экземпляр SSMS с помощью универсальной проверки подлинности Active Directory можно использовать только одну учетную запись Azure Active Directory.**  
    Это ограничение распространяется только на универсальную проверку подлинности Active Directory: вы можете входить на разные серверы, используя проверку пароля Active Directory, встроенную проверку подлинности Active Directory и проверку подлинности SQL Server.
    
    Чтобы обойти это ограничение, используйте другой экземпляр среды SSMS для входа в систему с другой учетной записью Azure Active Directory. 
    
4. **Команды платформы приложений уровня данных (DacFx) и конструктор схем в SSMS не поддерживают универсальную проверку подлинности Active Directory.**  
    Команды, использующие DacFx (например, команды импорта и экспорта) и конструктор схем в среде SSMS сейчас не поддерживают универсальную проверку подлинности Active Directory.
    
    Чтобы обойти это ограничение, используйте другие способы проверки подлинности, доступные в SSMS: проверку пароля Active Directory, встроенную проверку подлинности Active Directory и проверку подлинности SQL Server.

5. **Решение SSMS может подключаться только к экземплярам служб SQL Server 2016 Integrated Services (SSIS 2016).**  
    Мы знаем об ограниченной совместимости служб SQL Server Integration Services, которое не дает подключаться к предыдущим версиям.
    
    Чтобы временно решить эту проблему, подключитесь к экземпляру службы SQL Server Integration Service с помощью [выпуска SSMS, который соответствует вашему экземпляру SSIS](../ssms/previous-sql-server-management-studio-releases.md). 
  
5. **SSMS не сохраняет планы обслуживания для решения SQL Server 2008 R2 и более ранних версий SQL Server.**  
    Мы надеемся устранить это ограничение в будущем. А пока вы сможете сохранять планы обслуживания с помощью выпуска [SSMS 2014](../ssms/previous-sql-server-management-studio-releases.md) .  
    
5. **Для локализованных версий SSMS может потребоваться установка дополнительного пакета безопасности.**  
При использовании локализованных версий SSMS [пакет обновления безопасности KB 2862966](https://support.microsoft.com/en-us/kb/2862966) требуется при установке на следующих платформах: Windows 8, Windows 7, Windows Server 2012 и Windows Server 2008 R2.

5. **При нажатии кнопки "Справка" или клавиши F1 справка не открывается**  
При нажатии кнопки "Справка" или клавиши F1 в некоторых средах отображается следующее сообщение: **Требуется новое приложение для открытия ms-xhelp**. Эта ошибка является известной проблемой и будет устранена в будущей версии.
  
<a id="feedback" class="xliff"></a>

## Отзывы  
  
![needhelp_person_icon](../ssms/media/needhelp_person_icon.png) [форум клиентских средств SQL](https://social.msdn.microsoft.com/Forums/en-US/home?forum=sqltools) |  [Опубликуйте информацию о проблеме или предложение на Microsoft Connect](https://connect.microsoft.com/SQLServer/Feedback).  
  
<a id="see-also" class="xliff"></a>

## См. также:  
[Учебник по среде SQL Server Management Studio](../ssms/use-sql-server-management-studio.md)  
[Скачивание SQL Server Management Studio (службы SSMS)](../ssms/download-sql-server-management-studio-ssms.md)  
[Предыдущие выпуски SQL Server Management Studio](../ssms/previous-sql-server-management-studio-releases.md)  

  

