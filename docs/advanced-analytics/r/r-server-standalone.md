---
title: "R Server (изолированная версия) | Документация Майкрософт"
ms.custom:
- SQL2016_New_Updated
ms.date: 06/22/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
vms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- R
ms.assetid: ca9e48f1-67b8-4905-9b78-56752d7a4e81
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.openlocfilehash: 3f0c567463c25a54829a988516890bead171f5ec
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2018
---
# <a name="r-server-standalone"></a>R Server (Standalone)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В SQL Server 2016. Корпорация Майкрософт выпустила **R Server (изолированный)**, в состав платформы для поддержки аналитики корпоративного уровня.  Microsoft R Server обеспечивает масштабируемость и безопасность для языка R и обходит ограничения в памяти с открытым кодом R. Как SQL Server R Services Microsoft R Server (изолированный) предоставляет параллельной и фрагментированной обработки данных, позволяя пользователям использовать намного больше, чем может поместиться в памяти данных R.

В SQL Server 2017 г была добавлена поддержка для языка Python, с удовольствием широкая поддержка в сообществе машины обучения и содержит популярные библиотеки для анализа текста и углубленного обучения.  Чтобы отразить это более широкий набор языков, мы также переименовали его **Microsoft машины обучения Server (изолированный)**.

## <a name="benefits-of-microsoft-r-server"></a>Преимущества Microsoft R Server

Можно использовать Microsoft R Server для распределенных вычислений на нескольких платформах. При установке из программы установки SQL Server, вы получаете сервер под управлением Windows и все необходимые средства для развертывания и публикации моделей. Дополнительные сведения о других платформ см. в разделах в библиотеке MSDN:

+ [Introducing Microsoft R Server](https://msdn.microsoft.com/microsoft-r/rserver) (Знакомство с Microsoft R Server)
+ [R Server for Windows](https://msdn.microsoft.com/microsoft-r/rserver-install-windows) (R Server для Windows)

Можно также установить Microsoft R Server для использования в качестве клиента разработки, чтобы получить RevoScaleR библиотеки и средства, необходимые для создания решения R, которые могут быть развернуты в SQL Server.

## <a name="whats-new-in-microsoft-machine-learning-server"></a>Новые возможности Microsoft Server обучения машины

При установке службы обучения машины (автономный) с помощью программы установки SQL Server 2017 г. вы теперь можете Добавление языка Python. Естественно языка R по-прежнему поддерживается, и при необходимости можно даже установить оба языка.
 
В SQL Server 2017 г CTP 2.0 установки сервера включает пакет mrsdeploy и другим программам, используется для моделей, ввод в эксплуатацию. Дополнительные сведения см. в разделе [ввода в эксплуатацию с mrsdeploy](../../advanced-analytics/operationalization-with-mrsdeploy.md).

Корпоративные пользователи SQL Server машинного обучения можно использовать загружаемый установщики для Microsoft R Server для обновления их компоненты R, в процессе, называемом привязки. Дополнительные сведения см. в разделе [SqlBindR используется для обновления и экземпляра SQL Server](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)

## <a name="get-microsoft-r-server-or-machine-learning-server-standalone"></a>Получить Microsoft R Server или машины обучения Server (изолированный)

 Существует несколько параметров для установки Microsoft R Server.

+ Используйте мастер установки SQL Server

  [Создание изолированного сервера R Server](../r/create-a-standalone-r-server.md)

  Запустите программу установки SQL Server 2016 **Microsoft R Server (изолированный)**. Язык R добавляется по умолчанию.
  Или запустите программу установки SQL Server 2017 г. **машины обучения Server (изолированный)** и выберите R или Python или оба.

  > [!IMPORTANT]
  > Параметр, чтобы установить сервер находится в **Общие средства** части программы установки. Не устанавливайте другие компоненты.
  >
  > Лучше всего не следует устанавливать сервер на компьютере, где установлен SQL Server R Services или службы SQL Server машины обучения.

+ Использовать параметры командной строки для программы установки SQL Server

  [Установка Microsoft R Server из командной строки](../r/install-microsoft-r-server-from-the-command-line.md)

  Программа установки SQL Server поддерживает автоматической установки посредством широкий набор аргументов командной строки.

+ Используйте автономный установщик

  [Запустите Microsoft R Server для Windows](https://msdn.microsoft.com/microsoft-r/rserver-install-windows).

  Теперь можно использовать новый установщик Windows, чтобы установить новый экземпляр Microsoft R Server или Microsoft машины обучения.  Microsoft R Server (и обучения машины Microsoft Server) требуется соглашения SQL Server Enterprise. Однако после запуска автономного установщика политика поддержки для существующей установки обновляются для использования новой политики современных жизненного цикла. Этот параметр поддержки гарантирует обновления компонентов обучения машины применяются чаще, чем при использовании службы выпусках SQL Server.

  
+ Обновите экземпляр SQL Server

  [С помощью SqlBindR, чтобы обновить экземпляр служб R](./use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).
  
  Автономный установщик можно использовать для обновления экземпляра служб SQL Server 2016 R для использования последней версии R. При запуске установщика будет применена политика поддержки жизненного цикла современных на сервер, а компоненты R получит более частые обновления.
  
  > [! Примечание} в настоящее время этот метод обновления доступен только для существующих установок SQL Server 2016. Тем не менее обновление будет поддерживаться для 2017 г. SQL Server в будущем.

## <a name="related-machine-learning-products"></a>Связанные машинного обучения продуктов

+ Виртуальные машины Azure с R Server

  [Подготовка виртуальной машины сервера R](../../advanced-analytics/r-services/provision-the-r-server-only-sql-server-2016-enterprise-vm-on-azure.md)
  
  Azure marketplace включает в себя несколько образов виртуальных машин, которые включают R Server. Создание новой виртуальной машины R Server в Microsoft Azure является самым быстрым способом настройки сервера для использования в разработке и развертывании прогнозных моделей. Получены с возможностями масштабирования и общего доступа к уже настроена, которых облегчает внедрение аналитики R в приложениях и интеграции R с серверной системы.

+ Виртуальная машина анализа данных

  [Виртуальная машина анализа данных — Windows 2016 Preview](http://aka.ms/dsvm/win2016)

  Последнюю версию данных обработки и анализа виртуальной машины включает R Server, SQL Server, и массив наиболее популярных средств для машинного обучения, все предварительно и протестирован. Можно создавать записные книжки Jupyter разработки решений в Юлии и использовать библиотеки поддержкой GPU углубленного обучения как MXNet, CNTK и TensorFlow.

## <a name="resources"></a>Ресурсы

Примеры, учебники и Дополнительные сведения о сервере Microsoft R см. в разделе [продукты Microsoft R](https://msdn.microsoft.com/microsoft-r/microsoft-r-getting-started).

## <a name="see-also"></a>См. также

 [Службы R SQL Server](../../advanced-analytics/r/sql-server-r-services.md)

