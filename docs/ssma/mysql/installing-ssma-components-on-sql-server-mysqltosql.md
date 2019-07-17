---
title: Установка компонентов SSMA в SQL Server (MySQLToSql) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- SSMA extension pack, Installation
ms.assetid: 6772d0c5-258f-4d7b-afb0-b5f810e71af1
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 64040f4a0caf8253e6d6e8a3b00ff21e0cebe6d9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68075350"
---
# <a name="installing-ssma-components-on-sql-server-mysqltosql"></a>Установка компонентов SSMA в SQL Server (MySQLToSql)
Помимо установки SSMA, необходимо также установить компоненты на компьютере, на котором выполняется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эти компоненты включают пакет расширений SSMA, которая поддерживает перенос данных и поставщики MySQL, чтобы обеспечить подключение между серверами.  
  
## <a name="ssma-for-mysql-extension-pack"></a>SSMA для MySQL Extension Pack  
Пакет расширений SSMA добавляет базу данных, **sysdb**, для указанного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эта база данных содержит таблицы и хранимые процедуры, которые необходимы для переноса данных.  
  
Кроме того, при переносе данных для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], создает SSMA [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] задания агента, когда модуль переноса данных на стороне сервера используется для переноса данных.  
  
### <a name="prerequisites"></a>предварительные требования  
Перед установкой SSMA для MySQL серверные компоненты на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], убедитесь, что компьютер соответствует следующим требованиям:  
  
-   Установщик [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows версии 3.1 или более поздняя версия.  
  
-   Поставщик клиента MySQL и подключение к базе данных MySQL, которые требуется перенести. Поставщики можно установить с носителя продукта MySQL или MySQL веб-сайта.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Во время установки, должна быть запущена служба браузера. Используется для заполнения списка экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в мастере установки. Вы можете отключить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] служба браузера после установки.  
  
    > [!NOTE]  
    > Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] служба браузера запущена, но вы по-прежнему не видите списка экземпляров в программе установки, необходимо разблокировать порт UDP 1434. Чтобы временно разблокировать порт можно использовать брандмауэр Windows, или можно временно отключить брандмауэр Windows. Кроме того, может потребоваться временно отключить антивирусную программу. Не забудьте включить брандмауэров и антивирусного программного обеспечения после установки.  
  
### <a name="installing-the-extension-pack"></a>Установка пакета расширения  
Пакет расширений можно установить любое время, прежде чем переносить данные [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
> Чтобы установить пакет расширения, необходимо быть членом **sysadmin** роли сервера на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
**Чтобы установить пакет расширений**  
  
1.  Скопируйте SSMA для MySQL Extension Pack. *n*. Install.exe, где *n* — номер сборки, на компьютер, на котором выполняется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  Дважды щелкните SSMA для MySQL Extension Pack. *n*. Install.exe.  
  
3.  В диалоговом окне приветствия щелкните **Далее**.  
  
4.  В диалоговом окне лицензионного соглашения Прочитайте лицензионное соглашение. Если вы согласны, установите **я принимаю условия лицензионного соглашения** флажок и нажмите кнопку **Далее**.  
  
5.  В диалоговом окне Выбор типа установки нажмите кнопку **обычные**.  
  
6.  На все готово для установки диалоговое окно, нажмите кнопку **установить**.  
  
7.  На Completed диалоговое окно первого шага установки, нажмите кнопку **Далее**.  
  
    Появится новое диалоговое окно, в котором можно выбрать экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для установки пакета расширения.  
  
8.  Выберите экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] где вам будет миграции схемы MySQL, а затем нажмите кнопку **Далее**.  
  
    Экземпляр по умолчанию имеет имя, совпадающее с именем компьютера. Именованные экземпляры будут следовать обратную косую черту и имя экземпляра.  
  
9. В диалоговом окне подключения, выберите метод проверки подлинности и нажмите кнопку **Далее**.  
  
    Проверка подлинности Windows будет использовать учетные данные Windows для входа на экземпляр объекта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. При выборе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности, необходимо ввести [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имя входа и пароль.  
  
10. В следующем диалоговом окне выберите **установить базы данных служебных программ** *n*, где *n* — это номер версии, а затем нажмите кнопку **Далее**.  
  
    **Sysdb** база данных создается с помощью таблицы и хранимые процедуры, необходимые для переноса данных (с помощью модуль переноса данных на стороне сервера) создаются в этой базе данных.  
  
11. Чтобы установить служебные программы с другим экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]выберите **Да**и нажмите кнопку **Далее**. Чтобы выйти из мастера, нажмите кнопку **нет**.  
  
## <a name="see-also"></a>См. также  
[Установка SSMA для MySQL клиента &#40;MySQLToSQL&#41;](../../ssma/mysql/installing-ssma-for-mysql-client-mysqltosql.md)  
[Миграция MySQL базы данных в SQL Server — база данных Azure SQL &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
