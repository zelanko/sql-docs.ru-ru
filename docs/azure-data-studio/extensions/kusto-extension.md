---
title: Расширение Kusto (KQL) для Azure Data Studio
description: В этой статье описывается, как подключиться к кластерам Azure Data Explorer и выполнять запросы к ним с помощью Azure Data Studio.
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.reviewer: jukoesma
ms.custom: ''
ms.date: 10/29/2020
ms.openlocfilehash: 0c77b957f14401aec3130fa5fa4f78f0d34de9b5
ms.sourcegitcommit: 894c1a23e922dc29b82c1d2c34c7b0ff28b38654
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/30/2020
ms.locfileid: "93067206"
---
# <a name="kusto-kql-extension-for-azure-data-studio-preview"></a>Расширение Kusto (KQL) для Azure Data Studio (предварительная версия)

Расширение Kusto (KQL) для [Azure Data Studio](../what-is-azure-data-studio.md) позволяет подключаться к кластерам [Azure Data Explorer](/azure/data-explorer/data-explorer-overview) и выполнять к ним запросы.

Теперь пользователи могут создавать и выполнять запросы KQL, а также разрабатывать записные книжки с помощью [ядра Kusto](../notebooks/notebooks-kusto-kernel.md) с технологией IntelliSense.

Включив встроенный интерфейс Kusto (KQL) в Azure Data Studio, инженеры данных, аналитики данных и специалисты по обработке и анализу данных могут быстро отслеживать тенденции и аномалии в больших объемах хранимых данных в Azure Data Explorer.

Сейчас это расширение находится в режиме предварительной версии.

## <a name="prerequisites"></a>Предварительные требования

Если у вас еще нет подписки Azure, создайте [бесплатную учетную запись](https://azure.microsoft.com/free/) Azure, прежде чем начинать работу.

Также необходимы следующие компоненты.

- [Установленное решение Azure Data Studio](../download-azure-data-studio.md).
- [Кластер и база данных Azure Data Explorer](/azure/data-explorer/create-cluster-database-portal).

## <a name="install-the-kusto-kql-extension"></a>Установка расширения Kusto (KQL)

Чтобы установить расширение Kusto (KQL) в Azure Data Studio, выполните следующие действия.

1. Откройте диспетчер расширений в Azure Data Studio. Для этого можно щелкнуть значок "Расширения" или выбрать пункт **Расширения** в меню "Вид".

2. В строке поиска введите *Kusto*.

3. Выберите расширение **Kusto (KQL)** и просмотрите сведения о нем.

4. Выберите пункт **Установить**.

:::image type="content" source="media/kusto-extension/kusto-extension-icon.png" alt-text="Расширение Data Explorer":::

## <a name="how-to-connect-to-an-azure-data-explorer-cluster"></a>Порядок подключения к кластеру Azure Data Explorer

### <a name="find-your-azure-data-explorer-cluster"></a>Поиск кластера Azure Data Explorer

Найдите свой кластер Azure Data Explorer на [портале Azure](https://ms.portal.azure.com/#home), а затем найдите универсальный код ресурса (URI) для кластера.

:::image type="content" source="media/kusto-extension/kusto-extension-adx-cluster-uri.png" alt-text="URI":::

Вы также можете сразу приступить к работе, используя кластер *help.kusto.windows.net*.

В этой статье мы используем для примеров данные из кластера help.kusto.windows.net.

### <a name="connection-details"></a>Сведения о подключении

Чтобы настроить кластер Azure Data Explorer для подключения, выполните следующие действия.

1. Выберите **Создать подключение** в панели **Подключения**.

2. Заполните раздел **Сведения о подключении**.
    1. В качестве **типа соединения** выберите *Kusto*.
    2. В качестве **кластера** введите свой кластер Azure Data Explorer.

        > [!Note]
        > При вводе имени кластера не указывайте префикс `https://` и конечный `/`.

    3. В поле **Тип проверки подлинности** используйте значение по умолчанию — *Учетная запись Active Directory — универсальная с поддержкой MFA*.
    4. В поле **Учетная запись** укажите сведения о вашей учетной записи.
    5. В поле **База данных** укажите *По умолчанию*.
    6. В поле **Группа серверов** укажите *По умолчанию*.
        1. Это поле можно использовать, чтобы объединить ваши серверы в определенную группу.
    7. Поле **Имя (необязательно)** оставьте пустым.
        1. Это поле можно использовать для присвоения псевдонима вашему серверу.

    :::image type="content" source="media/kusto-extension/kusto-extension-connection-details.png" alt-text="Сведения о подключении":::

## <a name="how-to-query-an-azure-data-explorer-database-in-azure-data-studio"></a>Как выполнить запрос к базе данных Azure Data Explorer в Azure Data Studio

Теперь, когда вы настроили подключение к кластеру Azure Data Explorer, можно выполнять запросы к вашей базе данных с помощью Kusto (KQL).

Чтобы создать новую вкладку запроса, можно либо выбрать в меню **Файл > Создать запрос** , либо использовать сочетание клавиш *Ctrl + N* , либо щелкнуть базу данных правой кнопкой мыши и выбрать пункт **Создать запрос**.

Когда новая вкладка запроса будет открыта, введите запрос Kusto.

Ниже приведено несколько примеров запросов KQL.

```kusto
StormEvents
| limit 1000
```

```kusto
StormEvents
| where EventType == "Waterspout"
```

Дополнительные сведения о создании запросов KQL см. в статье [Написание запросов для Azure Data Explorer](/azure/data-explorer/write-queries#overview-of-the-query-language)

## <a name="view-extension-settings"></a>Просмотр параметров расширения

Чтобы изменить параметры расширения Kusto, выполните следующие действия.

1. Откройте диспетчер расширений в Azure Data Studio. Для этого можно щелкнуть значок "Расширения" или выбрать пункт **Расширения** в меню "Вид".

2. Найдите расширение **Kusto (KQL)** .

3. Щелкните значок **Управление**.

4. Щелкните значок **Параметры расширения**.

Параметры расширения выглядят следующим образом.

:::image type="content" source="media/kusto-extension/kusto-extension-settings.png" alt-text="Параметры расширения Kusto (KQL)":::

## <a name="sanddance-visualization"></a>Визуализация SandDance

[Расширение SandDance](sanddance-extension.md) с расширением Kusto (KQL) в Azure Data Studio объединяют сводят вместе широкие возможности интерактивной визуализации. В результирующем наборе запроса KQL нажмите кнопку **Визуализатор** , чтобы запустить [SandDance](https://sanddance.js.org/).

:::image type="content" source="media/kusto-extension/kusto-extension-sanddance-demo.gif" alt-text="Визуализация SandDance":::

## <a name="known-issues"></a>Известные проблемы

| Сведения | Обходной путь |
|---------|------------|
| [В записной книжке Kusto изменение подключения к базе данных на сохраненном подключении псевдонима зависает после ошибки при выполнении ячейки кода](https://github.com/microsoft/azuredatastudio/issues/12384) | Закройте и снова откройте записную книжку, а затем подключитесь к нужному кластеру с базой данных |
| [В записной книжке Kusto не работает изменение подключения к базе данных на несохраненном псевдониме](https://github.com/microsoft/azuredatastudio/issues/12843) |Создайте новое подключение во вьюлете подключений и сохраните его с псевдонимом. Затем создайте новую записную книжку и подключитесь к только что сохраненному соединению. | 
| [В записной книжке Kusto раскрывающийся список баз данных не заполняется при создании нового подключения ADX](https://github.com/microsoft/azuredatastudio/issues/12666) | Создайте новое подключение во вьюлете подключений и сохраните его с псевдонимом. Затем создайте новую записную книжку и подключитесь к только что сохраненному соединению. |

Можно отправить [запрос функции](https://github.com/microsoft/azuredatastudio/issues/new?assignees=&labels=&template=feature_request.md&title=), чтобы оставить отзыв для команды специалистов по продукту.  
Можно сообщить об [ошибке](https://github.com/microsoft/azuredatastudio/issues/new?assignees=&labels=&template=bug_report.md&title=), чтобы оставить отзыв для команды специалистов по продукту.

## <a name="next-steps"></a>Дальнейшие действия

- [Создание и запуск записной книжки Kusto](../notebooks/notebooks-kusto-kernel.md)
- [Записная книжка Kqlmagic в Azure Data Studio](../notebooks/notebooks-kqlmagic.md)
- [Памятка по преобразованию из SQL в Kusto](/azure/data-explorer/kusto/query/sqlcheatsheet)
- [Что такое Azure Data Explorer?](/azure/data-explorer/data-explorer-overview)
- [Использование визуализации SandDance](https://sanddance.js.org/)
