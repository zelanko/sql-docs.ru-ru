---
title: Создание резервной копии главного ключа службы | Документация Майкрософт
ms.custom: ''
ms.date: 01/02/2019
ms.prod: sql
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- service master key [SQL Server], exporting
ms.assetid: f60b917c-6408-48be-b911-f93b05796904
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: 1fa730e1143516df2fe5f14c04afcbb9292ac67f
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "74957488"
---
# <a name="back-up-the-service-master-key"></a>Создание резервной копии главного ключа службы
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В этой статье описано, как выполнить резервное копирование главного ключа службы [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Главный ключ службы является корневым элементом иерархии шифрования. Поэтому необходимо создать его резервную копию, которая должна храниться в надежном месте. Создание такой резервной копии должно быть одной из первых задач администрирования, выполненных на сервере.  

## <a name="before-you-begin"></a>Перед началом  
  
### <a name="limitations-and-restrictions"></a>Ограничения  

- Главный ключ должен быть открыт и, таким образом, расшифрован, прежде чем производится его резервное копирование. Если он зашифрован с помощью главного ключа службы, то главный ключ не нужно открывать явным образом, но если главный ключ зашифрован только с помощью пароля, он должен быть явным образом открыт.  
  
- Рекомендуется создать резервную копию главного ключа сразу же после его создания и затем сохранить в надежном месте.  
  
## <a name="security"></a>безопасность  
  
### <a name="permissions"></a>Разрешения
Требует разрешения CONTROL для базы данных.  
  
## <a name="using-transact-sql"></a>Использование Transact-SQL  
  
### <a name="to-back-up-the-service-master-key"></a>Создание резервной копии главного ключа службы
  
1. В среде [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]установите соединение с экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , содержащим главный ключ службы, для которого необходимо создать резервную копию.  
  
2. Задайте пароль, который будет использоваться для шифрования главного ключа службы на носителе данных резервных копий. Пароль проходит проверку сложности. Дополнительные сведения см. в разделе [Политика паролей](../../../relational-databases/security/password-policy.md).  
  
3. Получите съемный носитель данных резервной копии для хранения главного ключа.  
  
4. Укажите каталог NTFS, в котором будет создана резервная копия главного ключа. В этом каталоге будет сохранен файл, созданный на следующем шаге. Он должен быть защищен с помощью списка управления доступом со строгими ограничениями.  
  
5. В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
6. На стандартной панели выберите пункт **Создать запрос**.  
  
7. Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```sql
    -- Creates a backup of the service master key.
    USE master;
    GO
    BACKUP SERVICE MASTER KEY TO FILE = 'c:\temp_backups\keys\service_master_ key'
        ENCRYPTION BY PASSWORD = '3dH85Hhk003GHk2597gheij4';
    GO
    ```  
  
    > [!NOTE]  
    > Путь к файлу ключа и пароль ключа (если он существует) будет отличаться от вышеуказанного. Убедитесь, что оба этих параметра соответствуют вашему серверу и ключу.
  
8. Скопируйте файл на носитель данных резервных копий и проверьте правильность копирования.  
  
9. Сохраните резервную копию в надежном месте вне системы.  

 Дополнительные сведения см. в разделах [OPEN MASTER KEY (Transact-SQL)](../../../t-sql/statements/open-master-key-transact-sql.md) и [BACKUP MASTER KEY (Transact-SQL)](../../../t-sql/statements/backup-master-key-transact-sql.md).  
