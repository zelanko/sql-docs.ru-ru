---
title: Использование приложений в кластерах больших данных
titleSuffix: SQL Server big data clusters
description: Использование приложения, развернутого в кластере больших данных SQL Server 2019 с помощью веб-службы RESTFUL (Предварительная версия).
author: jeroenterheerdt
ms.author: jterh
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: a2135ef64fb17eba62eab75b81739eda047167ab
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419506"
---
# <a name="consume-an-app-deployed-on-sql-server-big-data-cluster-using-a-restful-web-service"></a>Использование приложения, развернутого в SQL Server кластере больших данных с помощью веб-службы RESTFUL

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этой статье описывается, как использовать приложение, развернутое в кластере больших данных SQL Server 2019 с помощью веб-службы RESTFUL (Предварительная версия).

## <a name="prerequisites"></a>предварительные требования

- [Кластер больших данных SQL Server 2019](deployment-guidance.md)
- [Служебная программа командной строки мссклктл](deploy-install-azdata.md)
- Приложение, развернутое с помощью [аздата](big-data-cluster-create-apps.md) или [расширения развертывания приложения](app-deployment-extension.md)

## <a name="capabilities"></a>Речь

После развертывания приложения в кластере больших данных SQL Server 2019 (Предварительная версия) вы можете получить доступ к этому приложению и использовать его с помощью веб-службы RESTFUL. Это обеспечивает интеграцию этого приложения с другими приложениями или службами (например, мобильным приложением или веб-сайтом). В следующей таблице описаны команды развертывания приложения, которые можно использовать с **аздата** для получения сведений о веб-службе RESTful для приложения.

|Command |Описание |
|:---|:---|
|`azdata app describe` | Описание приложения. |

Справку `--help` по параметру можно получить, как показано в следующем примере:

```bash
azdata app describe --help
```

В следующих разделах описывается, как получить конечную точку для приложения и как работать с веб-службой RESTFUL для интеграции приложений.

## <a name="retrieve-the-endpoint"></a>Получение конечной точки

Команда **аздата приложения описывает** подробные сведения о приложении, включая конечную точку в кластере. Обычно это используется разработчиком приложения для создания приложения с помощью клиента Swagger и использования WebService для взаимодействия с приложением на основе RESTFUL.

Опишите приложение, выполнив команду, аналогичную следующей:

```bash
azdata app describe --name addpy --version v1
```

```json
{
  "input_param_defs": [
    {
      "name": "x",
      "type": "int"
    },
    {
      "name": "y",
      "type": "int"
    }
  ],
  "links": {
    "app": "https://10.1.1.3:30777/api/app/addpy/v1",
    "swagger": "https://10.1.1.3:30777/api/app/addpy/v1/swagger.json"
  },
  "name": "add-app",
  "output_param_defs": [
    {
      "name": "result",
      "type": "int"
    }
  ],
  "state": "Ready",
  "version": "v1"
}
```

Запишите IP-адрес`10.1.1.3` (в этом примере) и номер порта (`30777`) в выходных данных.

## <a name="generate-a-jwt-access-token"></a>Создание маркера доступа JWT

Чтобы получить доступ к веб-службе RESTFUL для приложения, которое вы развернули, сначала необходимо создать маркер доступа JWT. Откройте следующий URL-адрес в браузере: `https://[IP]:[PORT]/api/docs/swagger.json` используя IP-адрес и порт, которые вы получили `describe` , выполнив указанную выше команду. Вам потребуется войти в систему с теми же учетными данными, которые `azdata login`использовались для.

Вставьте содержимое `swagger.json` в [Редактор Swagger](https://editor.swagger.io) , чтобы понять, какие методы доступны.

![Swagger API](media/big-data-cluster-consume-apps/api_swagger.png)

Обратите `app` внимание на метод Get, а `token` также на метод POST. Так как проверка подлинности для приложений использует токены JWT, необходимо получить маркер My с помощью вашего любимого средства, чтобы выполнить запрос `token` POST к методу. Ниже приведен пример того, как именно это делается в [публикации](https://www.getpostman.com/).

![Пост. токен](media/big-data-cluster-consume-apps/postman_token.png)

В результате выполнения этого запроса будет выдаваться JWT `access_token`, который должен вызвать URL-адрес для запуска приложения.

## <a name="execute-the-app-using-the-restful-web-service"></a>Выполнение приложения с помощью веб-службы RESTFUL

> [!NOTE]
> При необходимости можно открыть URL-адрес `swagger` , который был возвращен при `azdata app describe --name [appname] --version [version]` выполнении в браузере, который должен быть похож на `https://[IP]:[PORT]/api/app/[appname]/[version]/swagger.json`. Вам потребуется войти в систему с теми же учетными данными, которые `azdata login`использовались для. Содержимое `swagger.json` можно вставить в [Редактор Swagger](https://editor.swagger.io). Вы увидите, что веб-служба предоставляет `run` метод. Также обратите внимание на базовый URL-адрес, отображаемый в верхней части страницы.

Вы можете использовать любимое средство для вызова `run` метода (`https://[IP]:30778/api/app/[appname]/[version]/run`), передав параметры в тексте запроса POST как JSON. В этом примере мы будем использовать [POST](https://www.getpostman.com/). Перед вызовом необходимо присвоить `Authorization` `Bearer Token` значение и вставить в токен, полученный ранее. В этом случае задается заголовок для запроса. См. снимок экрана ниже.

![Заголовков запуска после выполнения](media/big-data-cluster-consume-apps/postman_run_1.png)

Затем в тексте запросов передайте параметры в приложение, которое вы вызываете, и присвойте `content-type` свойству `application/json`значение:

![Тело запуска POST](media/big-data-cluster-consume-apps/postman_run_2.png)

При отправке запроса будут получены те же выходные данные, что и при запуске приложения с помощью `azdata app run`:

![Результат выполнения POST](media/big-data-cluster-consume-apps/postman_result.png)

Теперь приложение успешно вызвано через веб-службу. Для интеграции этой веб-службы в приложение можно выполнить аналогичные действия.

## <a name="next-steps"></a>Следующие шаги

Дополнительные примеры можно также просмотреть на странице [Примеры развертывания приложений](https://aka.ms/sql-app-deploy).

Дополнительные сведения о SQL Server кластерах больших данных см. в разделе [что такое кластеры больших данных SQL Server 2019?](big-data-cluster-overview.md).
