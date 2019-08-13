---
title: Развертывание в кластере kubeadm с одним узлом с помощью скрипта bash
titleSuffix: SQL Server big data clusters
description: Используйте скрипт развертывания bash для развертывания кластера больших данных SQL Server 2019 (предварительная версия) в кластере kubeadm с одним узлом.
author: mihaelablendea
ms.author: mihaelab
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 37017221b636146a003f8af8890c655ed605bca9
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/25/2019
ms.locfileid: "68473076"
---
# <a name="deploy-with-a-bash-script-to-a-single-node-kubeadm-cluster"></a>Развертывание в кластере kubeadm с одним узлом с помощью скрипта bash

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этом руководстве вы используете образец скрипта bash для развертывания кластера Kubernetes с одним узлом с помощью kubeadm и последующего развертывания в нем кластера больших данных SQL Server.  

## <a name="prerequisites"></a>предварительные требования

- Стандартная **серверная** виртуальная машина Ubuntu 18.04 или 16.04. Все зависимости настраиваются скриптом, который запускается из виртуальной машины.

  > [!NOTE]
  > Использование виртуальных машин Azure пока не поддерживается.

- Виртуальная машина должна иметь по крайней мере 8 ЦП, 64 ГБ ОЗУ и 100 ГБ места на диске. После получения всех образов Docker для кластера больших данных останется 50 ГБ для данных и журналов всех компонентов.

## <a name="instructions"></a>Instructions

1. Скачайте скрипт в виртуальную машину, которую планируете использовать для развертывания.

   ```bash
   curl --output setup-bdc.sh https://raw.githubusercontent.com/microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/deployment/kubeadm/ubuntu-single-node-vm/setup-bdc.sh
   ```

2. Преобразуйте скрипт в исполняемый файл с помощью приведенной ниже команды.

   ```bash
   chmod +x setup-bdc.sh
   ```

3. Выполните скрипт с использованием **sudo**.

   ```bash
   sudo ./setup-bdc.sh
   ```

   При появлении запроса введите пароль для следующих внешних конечных точек: контроллера, главного экземпляра SQL Server и шлюза. Имя пользователя по умолчанию для контроллера — *admin*.

4. Настройте псевдоним для средства **azdata**.

   ```bash
   source ~/.bashrc
   ```

5. Проверьте, работает ли псевдоним.

   ```bash
   azdata --version
   ```

## <a name="next-steps"></a>Следующие шаги

Чтобы приступить к использованию кластера больших данных, обратитесь к [этому руководству](tutorial-load-sample-data.md).
