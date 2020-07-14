---
title: Восстановление главного ключа базы данных | Документация Майкрософт
description: Узнайте, как восстановить главный ключ базы данных в SQL Server при помощи SQL Server Management Studio с Transact-SQL.
ms.custom: ''
ms.date: 01/02/2019
ms.prod: sql
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- database master key [SQL Server], importing
ms.assetid: 16897cc5-db8f-43bb-a38e-6855c82647cf
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: 9860b952751937b18ca5e95e92ac959bb86abd23
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85892243"
---
# <a name="restore-a-database-master-key"></a>Восстановление главного ключа базы данных
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  В этом разделе описывается, как восстановить главный ключ базы данных в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] при помощи [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
## <a name="before-you-begin"></a>Перед началом  
  
### <a name="limitations-and-restrictions"></a>Ограничения  
  
- Когда главный ключ восстановлен, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] дешифрует все ключи, зашифрованные текущим активным главным ключом, и затем шифрует эти ключи с помощью восстановленного главного ключа. Данную ресурсоемкую операцию следует планировать на то время, когда количество обращений к серверу минимальное. Если текущий главный ключ базы данных не открыт или не может быть открыт, или если какой-либо зашифрованный им ключ не может быть дешифрован, операция восстановления заканчивается неудачно.  
  
- Если во время расшифровки любого объекта произойдет ошибка, восстановление будет прервано. Чтобы пропускать ошибки, можно использовать параметр FORCE, но это приведет к потере всех данных, которые не удается расшифровать.  
  
- Если главный ключ был зашифрован главным сервисным ключом, восстановленный главный ключ также будет зашифрован главным сервисным ключом.  
  
- Если в текущей базе данных нет главного ключа, RESTORE MASTER KEY создает главный ключ. Новый главный ключ не будет автоматически шифроваться главным сервисным ключом.  
  
## <a name="security"></a>Безопасность  
  
### <a name="permissions"></a>Разрешения
Требует разрешения CONTROL для базы данных.  
  
## <a name="using-sql-server-management-studio-with-transact-sql"></a>В среде SQL Server Management Studio с помощью Transact-SQL  
  
### <a name="to-restore-the-database-master-key"></a>Восстановление главного ключа базы данных  
  
1. Сохраните резервную копию главного ключа базы данных с физического носителя данных резервных копий или из папки локальной файловой системы.  
  
2. В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
3. На стандартной панели выберите пункт **Создать запрос**.  
  
4. Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  

    ```sql
    -- Restores the database master key of the AdventureWorks2012 database.  
    USE AdventureWorks2012;  
    GO  
    RESTORE MASTER KEY   
        FROM FILE = 'c:\backups\keys\AdventureWorks2012_master_key'   
        DECRYPTION BY PASSWORD = '3dH85Hhk003#GHkf02597gheij04'   
        ENCRYPTION BY PASSWORD = '259087M#MyjkFkjhywiyedfgGDFD';  
    GO  
    ```  
  
    > [!NOTE]  
    > Путь к файлу ключа и пароль ключа (если он существует) будет отличаться от вышеуказанного. Убедитесь, что оба этих параметра соответствуют настройке конкретного сервера и ключа.  
  
 Дополнительные сведения см. в разделе [RESTORE MASTER KEY (Transact-SQL)](../../../t-sql/statements/restore-master-key-transact-sql.md)  
