---
title: Установка компонентов SSMA на SQL Server (MySQLToSql) | Документация Майкрософт
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68075350"
---
# <a name="installing-ssma-components-on-sql-server-mysqltosql"></a>Установка компонентов SSMA в SQL Server (MySQLToSql)
Помимо установки SSMA, необходимо также установить компоненты на компьютере, на котором выполняется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. К этим компонентам относится пакет расширений SSMA, который поддерживает миграцию данных, и поставщики MySQL для обеспечения подключения между серверами.  
  
## <a name="ssma-for-mysql-extension-pack"></a>Пакет расширений SSMA для MySQL  
Пакет расширений SSMA добавляет базу данных **сисдб**к указанному экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эта база данных содержит таблицы и хранимые процедуры, необходимые для переноса данных.  
  
Кроме того, при переносе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]в SSMA создает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] задания агента, когда для переноса данных используется модуль миграции данных на стороне сервера.  
  
### <a name="prerequisites"></a>Предварительные требования  
Перед установкой SSMA для серверных компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]MySQL убедитесь, что компьютер соответствует следующим требованиям.  
  
-   Установщик [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows версии 3.1 или более поздняя версия.  
  
-   Поставщик клиента MySQL и подключение к базе данных MySQL, которую необходимо перенести. Вы можете установить поставщики с носителя продукта MySQL или с веб-сайта MySQL.  
  
-   Служба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] браузера должна быть запущена во время установки. Используется для заполнения списка экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в мастере установки. Службу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] браузера можно отключить после установки.  
  
    > [!NOTE]  
    > Если служба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] браузера запущена, но список экземпляров в программе установки по-прежнему не отображается, необходимо разблокировать UDP-порт 1434. Вы можете использовать брандмауэр Windows, чтобы временно разблокировать порт, или временно отключить брандмауэр Windows. Также может потребоваться временное отключение антивирусного по. После установки обязательно включите брандмауэры и антивирусное по.  
  
### <a name="installing-the-extension-pack"></a>Установка пакета расширений  
Пакет расширений можно установить в любое время перед переносом данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
> Чтобы установить пакет расширений, необходимо быть членом роли сервера **sysadmin** на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
**Установка пакета расширений**  
  
1.  Скопируйте SSMA для пакета расширения MySQL. *n*. Install. exe, где *n* — номер сборки, на компьютер, на котором работает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  Дважды щелкните SSMA для пакета расширений MySQL. *n*. Install. exe.  
  
3.  В диалоговом окне Добро пожаловать нажмите кнопку **Далее**.  
  
4.  Ознакомьтесь с лицензионным соглашением в диалоговом окне Лицензионное соглашение. Если вы согласны, установите флажок **я принимаю условия лицензионного соглашения** и нажмите кнопку **Далее**.  
  
5.  В диалоговом окне Выбор типа установки выберите вариант **Обычная**.  
  
6.  В диалоговом окне все готово для установки нажмите кнопку **установить**.  
  
7.  В диалоговом окне «Завершение первого шага установки» нажмите кнопку **Далее**.  
  
    Появится новое диалоговое окно, в котором будет выбран экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для установки пакета расширений.  
  
8.  Выберите экземпляр, на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] котором будут перенесены схемы MySQL, и нажмите кнопку **Далее**.  
  
    Имя экземпляра по умолчанию совпадает с именем компьютера. За именованными экземплярами будет следовать обратная косая черта и имя экземпляра.  
  
9. В диалоговом окне Подключение выберите метод проверки подлинности и нажмите кнопку **Далее**.  
  
    При проверке подлинности Windows будут использоваться учетные данные Windows для входа на экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. При выборе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности необходимо ввести имя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа и пароль.  
  
10. В следующем диалоговом окне выберите **установить служебные базы данных** *n*, где *n* — номер версии, а затем нажмите кнопку **Далее**.  
  
    База данных **сисдб** создается с таблицами и хранимыми процедурами, необходимыми для переноса данных (с использованием сервера серверной части данных) в этой базе данных.  
  
11. Чтобы установить служебные программы на другой экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], выберите **Да**, а затем нажмите кнопку **Далее**. Чтобы выйти из мастера, нажмите кнопку **нет**.  
  
## <a name="see-also"></a>См. также:  
[Установка SSMA для клиента MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/installing-ssma-for-mysql-client-mysqltosql.md)  
[Перенос баз данных MySQL в SQL Server Azure SQL DB &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
