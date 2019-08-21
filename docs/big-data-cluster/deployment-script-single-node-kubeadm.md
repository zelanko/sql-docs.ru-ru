---
title: Развертывание в кластере kubeadm с одним узлом с помощью скрипта bash
titleSuffix: SQL Server big data clusters
description: Используйте скрипт развертывания bash для развертывания [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] в кластере кубеадм с одним узлом.
author: mihaelablendea
ms.author: mihaelab
ms.reviewer: mikeray
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: f6b6581eacad2fa9a65f64fdc29d6dfcde53852a
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/20/2019
ms.locfileid: "69652344"
---
# <a name="deploy-with-a-bash-script-to-a-single-node-kubeadm-cluster"></a>Развертывание в кластере kubeadm с одним узлом с помощью скрипта bash

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этом руководстве вы используете образец скрипта bash для развертывания кластера Kubernetes с одним узлом с помощью kubeadm и последующего развертывания в нем кластера больших данных SQL Server.  

## <a name="prerequisites"></a>Предварительные требования

- Виртуальный или физический компьютер обычный Ubuntu 18,04 или 16,04. Все зависимости настраиваются скриптом, который запускается из виртуальной машины.

  > [!NOTE]
  > Использование виртуальных машин Linux в Azure пока не поддерживается.

- Виртуальная машина должна иметь по меньшей мере 8 ЦП, 64 ГБ ОЗУ и 100 ГБ дискового пространства. После получения всех образов Docker для кластера больших данных останется 50 ГБ для данных и журналов всех компонентов.

- Обновите существующие пакеты с помощью приведенных ниже команд, чтобы убедиться, что образ ОС обновлен.

   ``` bash
   sudo apt update&&apt upgrade -y
   sudo systemctl reboot
   ```

## <a name="recommended-virtual-machine-settings"></a>Рекомендуемые параметры виртуальной машины

1. Используйте конфигурацию статической памяти для виртуальной машины. Например, в установках Hyper-V не используется динамическое выделение памяти, а вместо этого выделяется рекомендуемый 64 ГБ или выше.

1. Используйте возможность создания контрольных точек или моментальных снимков в гипервизоре Hyper, чтобы выполнить откат виртуальной машины до чистого состояния.


## <a name="instructions-to-deploy-sql-server-big-data-cluster"></a>Инструкции по развертыванию SQL Server кластера больших данных

1. Скачайте скрипт в виртуальную машину, которую планируете использовать для развертывания.

   ```bash
   curl --output setup-bdc.sh https://raw.githubusercontent.com/microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/deployment/kubeadm/ubuntu-single-node-vm/setup-bdc.sh
   ```

2. Преобразуйте скрипт в исполняемый файл с помощью приведенной ниже команды.

   ```bash
   chmod +x setup-bdc.sh
   ```

3. Запустите сценарий (убедитесь, что выполняется с помощью *sudo*).

   ```bash
   sudo ./setup-bdc.sh
   ```

   При появлении запроса введите пароль для следующих внешних конечных точек: контроллера, главного экземпляра SQL Server и шлюза. Пароль должен быть достаточно сложным в зависимости от существующих правил для SQL Server пароля. Имя пользователя по умолчанию для контроллера — *admin*.

4. Настройте псевдоним для средства **azdata**.

   ```bash
   source ~/.bashrc
   ```

5. Обновите настройки псевдонима для аздата.

   ```bash
   azdata --version
   ```

## <a name="cleanup"></a>Очистка

Сценарий [Cleanup-BDC.sh](https://raw.githubusercontent.com/microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/deployment/kubeadm/ubuntu-single-node-vm/cleanup-bdc.sh) предоставляется в качестве удобства для сброса среды, если это необходимо. Однако рекомендуется использовать виртуальную машину для тестирования и использовать возможности создания моментальных снимков в гипервизоре для отката виртуальной машины до чистого состояния.

## <a name="next-steps"></a>Следующие шаги

Чтобы приступить к работе с кластерами больших данных [, см. раздел учебник. Загрузка демонстрационных данных в SQL Server кластер](tutorial-load-sample-data.md)больших данных.
