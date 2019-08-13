---
title: Использование приложений в кластерах больших данных
titleSuffix: SQL Server big data clusters
description: Использование приложения, развернутого в кластере больших данных SQL Server 2019, с помощью веб-службы на базе REST (предварительная версия).
author: jeroenterheerdt
ms.author: jterh
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: a2135ef64fb17eba62eab75b81739eda047167ab
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/25/2019
ms.locfileid: "68419506"
---
# <a name="consume-an-app-deployed-on-sql-server-big-data-cluster-using-a-restful-web-service"></a>Использование приложения, развернутого в кластере больших данных SQL Server, с помощью веб-службы на базе REST

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Эта статья описывает использование приложения, развернутого в кластере больших данных SQL Server 2019, с помощью веб-службы на базе REST (предварительная версия).

## <a name="prerequisites"></a>предварительные требования

- [Кластер больших данных SQL Server 2019](deployment-guidance.md)
- [Служебная программа командной строки mssqlctl](deploy-install-azdata.md)
- Приложение, развернутое с помощью [azdata](big-data-cluster-create-apps.md) или [расширения развертывания приложения](app-deployment-extension.md)

## <a name="capabilities"></a>Возможности

После развертывания приложения в кластере больших данных SQL Server 2019 (предварительная версия) вы можете обращаться к этому приложению и использовать его с помощью веб-службы на основе REST. Это обеспечивает интеграцию этого приложения с другими приложениями или службами (например, мобильным приложением или веб-сайтом). В следующей таблице описаны команды развертывания приложения, которые можно использовать с **azdata**, чтобы получить сведения о веб-службе на основе REST для приложения.

|Command |Описание |
|:---|:---|
|`azdata app describe` | Описание приложения. |

Справку по параметру `--help` можно получить, как показано в следующем примере.

```bash
azdata app describe --help
```

В следующих разделах описано, как получить конечную точку для приложения и работать с веб-службой на основе REST для интеграции приложений.

## <a name="retrieve-the-endpoint"></a>Получение конечной точки

Команда **azdata app describe** предоставляет подробные сведения о приложении, включая конечную точку в кластере. Обычно она используется разработчиком приложения, чтобы создать приложение с помощью клиента Swagger и использовать веб-службу для взаимодействия с приложением на основе REST.

Опишите приложение, выполнив команду, аналогичную следующей.

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

Запишите IP-адрес (в этом примере — `10.1.1.3`) и номер порта (`30777`) в выходных данных.

## <a name="generate-a-jwt-access-token"></a>Создание маркера доступа JWT

Чтобы обратиться к веб-службе на основе REST для развернутого приложения, сначала нужно создать маркер доступа JWT. Откройте следующий URL-адрес в браузере: `https://[IP]:[PORT]/api/docs/swagger.json`, используя IP-адрес и порт, которые вы получили при выполнении указанной выше команды `describe`. Вам потребуется войти в систему с теми же учетными данными, которые использовались для `azdata login`.

Вставьте содержимое `swagger.json` в [редактор Swagger](https://editor.swagger.io), чтобы понять, какие методы доступны.

![Swagger API](media/big-data-cluster-consume-apps/api_swagger.png)

Обратите внимание на метод GET `app`, а также на метод POST `token`. Так как проверка подлинности для приложений использует маркеры JWT, вам потребуется получить маркер с помощью привычного вам средства, чтобы выполнить запрос POST к методу `token`. Ниже приведен пример того, как именно это можно сделать в [Postman](https://www.getpostman.com/).

![Маркер Postman](media/big-data-cluster-consume-apps/postman_token.png)

Результат этого запроса предоставит вам `access_token` JWT, который потребуется при вызове URL-адреса для запуска приложения.

## <a name="execute-the-app-using-the-restful-web-service"></a>Выполнение приложения с помощью веб-службы на основе REST

> [!NOTE]
> При необходимости вы можете открыть URL-адрес для `swagger`, возвращенный при выполнении `azdata app describe --name [appname] --version [version]` в браузере, который должен быть похож на `https://[IP]:[PORT]/api/app/[appname]/[version]/swagger.json`. Вам потребуется войти в систему с теми же учетными данными, которые использовались для `azdata login`. Содержимое `swagger.json` можно вставить в [редактор Swagger](https://editor.swagger.io). Вы увидите, что веб-служба предоставляет метод `run`. Также обратите внимание на базовый URL-адрес, отображаемый сверху.

Вы можете использовать привычное средство для вызова метода `run` (`https://[IP]:30778/api/app/[appname]/[version]/run`), передав параметры в текст запроса POST в виде JSON. В этом примере мы будем использовать [Postman](https://www.getpostman.com/). Перед вызовом нужно задать для `Authorization` значение `Bearer Token` и вставить полученный ранее маркер. Этим вы зададите заголовок своего запроса. См. снимок экрана ниже.

![Заголовки выполнения Postman](media/big-data-cluster-consume-apps/postman_run_1.png)

Затем в тексте запросов передайте параметры в приложение, которое вы вызываете, и присвойте `content-type` значение `application/json`.

![Текст выполнения Postman](media/big-data-cluster-consume-apps/postman_run_2.png)

При отправке запроса вы получите те же выходные данные, что и при запуске приложения с помощью `azdata app run`.

![Результат выполнения Postman](media/big-data-cluster-consume-apps/postman_result.png)

Вы успешно вызвали приложение через веб-службу. Интегрировать эту веб-службы в свое приложение можно аналогичным образом.

## <a name="next-steps"></a>Следующие шаги

Дополнительные примеры можно просмотреть в наборе [примеров развертывания приложений](https://aka.ms/sql-app-deploy).

Дополнительные сведения о кластерах больших данных SQL Server см. в статье [Что такое кластеры больших данных SQL Server 2019?](big-data-cluster-overview.md)
