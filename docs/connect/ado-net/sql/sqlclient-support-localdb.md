---
title: Поддержка поставщика SqlClient для LocalDB
description: Сведения о поддержке в SqlClient баз данных LocalDB
ms.date: 08/15/2019
ms.assetid: cf796898-5575-46f2-ae6e-21e5aa8c4123
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: 189d0a2997b256f9c9b615fc81b5b9ed3ef46a5c
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80918724"
---
# <a name="sqlclient-support-for-localdb"></a>Поддержка поставщика SqlClient для LocalDB

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

Начиная с названия кода Denali в SQL Server, будет доступна облегченная версия SQL Server, называемая LocalDB. В этом разделе обсуждаются способы подключения к базе данных в LocalDB.  
  
## <a name="remarks"></a>Remarks  
Дополнительные сведения о LocalDB, включая способы его установки и настройки, см. в электронной документации на SQL Server.  
  
Чтобы получить сводные сведения о возможностях работы с LocalDB, выполните следующие действия.  
  
- Создайте и запустите экземпляры LocalDB с помощью sqllocaldb.exe или файла app.config.  
  
- Для добавления и изменения баз данных в локальном экземпляре LocalDB можно воспользоваться программой sqlcmd.exe. Например, `sqlcmd -S (localdb)\myinst`.  
  
- Используйте ключевое слово строки подключения `AttachDBFilename`, чтобы добавить базу данных в экземпляр LocalDB. Если при использовании `AttachDBFilename` не указано имя базы данных в ключевом слове строки подключения `Database`, то база данных будет удалена из экземпляра LocalDB при закрытии приложения.  
  
- Чтобы указать экземпляр LocalDB в строке подключения, выполните указанные ниже действия. Например, у вас есть экземпляр с именем `myInstance`, строка подключения будет включать:  
  
```console
server=(localdb)\\myInstance  
```  
  
`User Instance=True` не допускается при подключении к базе данных LocalDB.  
  
Базу данных LocalDB можно скачать из [пакета дополнительных компонентов Microsoft SQL Server 2012](https://www.microsoft.com/download/en/details.aspx?id=29065). Если необходимо изменение данных в экземпляре LocalDB с помощью программы sqlcmd.exe, то необходимо пользоваться версией sqlcmd из SQL Server 2012. Эту программу можно также получить из пакета дополнительных компонентов SQL Server 2012.  
  
## <a name="programmatically-create-a-named-instance"></a>Программное создание именованного экземпляра  
Приложение может создать именованный экземпляр и указать базу данных, как показано ниже.  
  
- Укажите экземпляры LocalDB, чтобы добавить в файл app.config сведения, как показано ниже.  Номер версии экземпляра должен совпадать с номером версии установки LocalDB.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <configSections>  
        <section  
        name="system.data.localdb"  
        type="System.Data.LocalDBConfigurationSection,System.Data,Version=4.0.0.0,Culture=neutral,PublicKeyToken=b77a5c561934e089"/>  
      </configSections>  
      <system.data.localdb>  
        <localdbinstances>  
          <add name="myInstance" version="11.0" />  
        </localdbinstances>  
      </system.data.localdb>  
    </configuration>  
    ```  
  
- Укажите имя экземпляра с помощью ключевого слова строки подключения `server`.  Имя экземпляра, указанное в ключевом слове строки подключения `server`, должно соответствовать имени, указанному в файле app.config.  
  
- Используйте ключевое слово строки подключения `AttachDBFilename`, чтобы указать MDF-файл.  
  
## <a name="next-steps"></a>Дальнейшие действия
- [Функции SQL Server и ADO.NET](sql-server-features-adonet.md)
