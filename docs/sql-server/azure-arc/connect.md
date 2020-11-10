---
title: Подключение к Azure Arc
titleSuffix: ''
description: Подключение экземпляра SQL Server к Azure Arc
author: anosov1960
ms.author: sashan
ms.reviewer: mikeray
ms.date: 09/10/2020
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: e80892bfef7ee2c8cf22aef1b491ab5ea0c0addd
ms.sourcegitcommit: 442fbe1655d629ecef273b02fae1beb2455a762e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/03/2020
ms.locfileid: "93235568"
---
# <a name="connect-your-sql-server-to-azure-arc"></a>Подключение SQL Server к Azure Arc

Вы можете подключить локальный экземпляр SQL Server к службе Azure Arc, выполнив следующие действия.

## <a name="prerequisites"></a>Предварительные требования

* На компьютере должен быть установлен хотя бы один экземпляр SQL Server.
* На компьютерах с ОС Windows необходимо установить Azure PowerShell. Чтобы [установить Azure PowerShell](/powershell/azure/install-az-ps), следуйте следующей инструкции.
* На компьютерах с ОС Linux необходимо скачать Azure CLI и подключиться к учетной записи Azure. Чтобы [установить Azure CLI](/cli/azure/install-azure-cli-apt), следуйте следующей инструкции.
* Поставщик ресурсов **Microsoft.AzureData** зарегистрирован. Дополнительные сведения о поставщиках ресурсов Azure см. в "Поставщики и типы ресурсов Azure".
    * В PowerShell выполните команду `Register-AzResourceProvider -ProviderNamespace Microsoft.AzureData`.
    * В Linux выполните `az provider register --namespace 'Microsoft.AzureData`.



## <a name="generate-a-registration-script-for-sql-server"></a>Создание скрипта регистрации для SQL Server

На этом шаге вы создадите скрипт, который обнаруживает все экземпляры SQL Server, установленные на компьютере, и регистрирует их как ресурсы __SQL Server — Azure Arc__. Если физическая или виртуальная машина, на которой размещен экземпляр SQL Server, не зарегистрирована в службе Azure Arc, скрипт сделает это автоматически.

1. Найдите тип ресурса __SQL Server — Azure Arc__ и добавьте новый ресурс в колонке создания.

![Начало создания](media/join/start-creation-of-sql-server-azure-arc-resource.png)
    
2. Проверьте предварительные требования и перейдите на вкладку **Сведения о сервере**.  

3. Выберите подписку, группу ресурсов, регион Azure и операционную систему хост-компьютера. При необходимости укажите также прокси-сервер, используемый вашей сетью для подключения к Интернету.

> [!IMPORTANT]
> Если компьютер, на котором размещен экземпляр SQL Server, уже [подключен к службе Azure Arc](/azure/azure-arc/servers/onboard-portal), убедитесь, что выбрана та же группа ресурсов, которая содержит соответствующий ресурс __Компьютер — Azure Arc__.

![Сведения о сервере](media/join/server-details-sql-server-azure-arc.png)

4. Перейдите на вкладку **Запуск скрипта** и скачайте скрипт регистрации. Портал создает скрипт для указанной вами ОС размещения.

![Скачивание скрипта](media/join/download-script-sql-server-azure-arc.png)

## <a name="connect-the-installed-sql-server-instances-to-azure-arc"></a>Подключение установленных экземпляров SQL Server к службе Azure Arc

На этом шаге вы выполните скрипт, скачанный с портала Azure, на целевой физической или виртуальной машине. В результате каждый установленный экземпляр SQL Server на этом компьютере будет зарегистрирован как ресурс __SQL Server — Azure Arc__. Кроме того, если на компьютерах не установлен гостевой агент конфигурации, он будет установлен автоматически и зарегистрирован как ресурс __Компьютер — Azure Arc__.

> [!NOTE]
> Сценарий необходимо выполнять с использованием учетной записи, которая соответствует минимальным требованиям к разрешениям, описанным в разделе [Предварительные требования](overview.md#prerequisites).

### <a name="windows"></a>Windows

1. Запустите экземпляр администратора __powershell.exe__ и войдите в модуль PowerShell с помощью своих учетных данных Azure. Следуйте [инструкциям по входу](/powershell/azure/install-az-ps#sign-in).

2. Выполнение скачанного скрипта

   ```powershell
   & '.\RegisterSqlServerArc.ps1'
   ```

   > [!NOTE]
   > Если модуль AZ для PowerShell не был предварительно установлен, то при первом запуске возникнут проблемы. В таком случае выполните инструкции в скрипте, чтобы установить этот модуль и подключить свою учетную запись, а затем выполните скрипт снова.

### <a name="linux"></a>Linux

1. Используйте Azure CLI для входа со своими учетными данными Azure. Следуйте [инструкциям по входу](/cli/azure/authenticate-azure-cli).

2. Предоставьте скачанному скрипту разрешение на выполнение и выполните его.

   ```bash
   sudo chmod +x ./RegisterSqlServerArc.sh
   ./RegisterSqlServerArc.sh
   ```

## <a name="register-sql-server-instances-on-multiple-machines"></a>Регистрация экземпляров SQL Server на нескольких компьютерах

Вы можете подключить к Azure Arc несколько экземпляров SQL Server, установленных на нескольких компьютерах Windows или Linux, с помощью того же скрипта, который был создан для одного компьютера. Выполните инструкции по [масштабному подключению экземпляров SQL Server к Azure Arc](connect-at-scale.md).

## <a name="validate-the-sql-server---azure-arc-resources"></a>Проверка ресурсов SQL Server — Azure Arc

Перейдите на [портал Azure](https://ms.portal.azure.com/#home) и откройте только что зарегистрированный ресурс __SQL Server — Azure Arc__ , чтобы проверить его.

![Проверка подключенного экземпляра SQL Server ](media/join/validate-sql-server-azure-arc.png)

## <a name="un-register-the-sql-server---azure-arc-resources"></a>Отмена регистрации ресурсов SQL Server — Azure Arc

Чтобы удалить существующий ресурс __SQL Server — Azure Arc__ , перейдите в группу ресурсов, которая его содержит, и удалите его из списка ресурсов в этой группе.

![Отмена регистрации экземпляра SQL Server](media/join/delete-sql-server-azure-arc.png)

## <a name="next-steps"></a>Дальнейшие действия

* [Настройка расширенной защиты данных для экземпляра SQL Server](configure-advanced-data-security.md)

* [Настройка оценки SQL по запросу для экземпляра SQL Server](assess.md)