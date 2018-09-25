---
title: Восстановление главного ключа службы | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: vanto
ms.suite: sql
ms.technology: security
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- service master key [SQL Server], importing
- service master key [SQL Server], restoring
ms.assetid: 14bdbbbe-d384-4692-b670-4243d2466fe1
caps.latest.revision: 17
author: aliceku
ms.author: aliceku
manager: craigg
ms.openlocfilehash: 0b077bff2d86140de4da436d603798c7f14bce2c
ms.sourcegitcommit: 3762dd447ca4bb449eda8476e72f393db0851b38
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2018
ms.locfileid: "46013669"
---
# <a name="restore-the-service-master-key"></a>Восстановление главного ключа службы
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В этом разделе описывается, как восстановить главный ключ службы [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] при помощи [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
> [!WARNING]  
>  Маловероятно, что когда-нибудь потребуется восстановление главного ключа службы, Но если все же придется это делать, эту операцию следует выполнять предельно внимательно. Дополнительные сведения см. в статье [Back Up the Service Master Key](../../../relational-databases/security/encryption/back-up-the-service-master-key.md).  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [безопасность](#Security)  
  
-   [Восстановление главного ключа службы с помощью Transact-SQL](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   При восстановлении главного ключа службы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] расшифровывает все ключи и секретные коды, зашифрованные вместе с текущим главным ключом службы, а затем зашифровывает их вместе с восстановленным ключом из файла резервной копии.  
  
-   Если во время расшифровки любого объекта произойдет ошибка, восстановление будет прервано. Чтобы пропускать ошибки, можно использовать параметр FORCE, но это приведет к потере всех данных, которые не удается расшифровать.  
  
-   Повторное формирование иерархии шифрования — ресурсоемкая операция. Ее нужно назначить на период низкой нагрузки на сервер.  
  
> [!CAUTION]  
>  Главный ключ службы является корнем иерархии шифрования [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Этот ключ явно или неявно защищает все остальные ключи в дереве. Если зависящий от него ключ не может быть расшифрован, но восстановление продолжено, то данные, защищенные этим ключом, будут утеряны.  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Необходимо разрешение CONTROL SERVER на сервер.  
  
##  <a name="SSMSProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-restore-the-service-master-key"></a>Восстановление главного ключа службы  
  
1.  Сохраните резервную копию главного ключа службы с физического носителя данных резервных копий или из папки локальной файловой системы.  
  
2.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
3.  На стандартной панели выберите пункт **Создать запрос**.  
  
4.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    -- Restores the service master key from a backup file.  
    RESTORE SERVICE MASTER KEY   
        FROM FILE = 'c:\temp_backups\keys\service_master_key'   
        DECRYPTION BY PASSWORD = '3dH85Hhk003GHk2597gheij4';  
    GO  
    ```  
  
    > [!NOTE]  
    >  Путь к файлу ключа и пароль ключа (если он существует) будет отличаться от вышеуказанного. Убедитесь, что оба этих параметра соответствуют настройке конкретного сервера и ключа.  
  
  
