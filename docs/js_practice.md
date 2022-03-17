# Best Practice of JavaScript


* Prevent using `Promises` within `map()`.
    
    **<font color=#b00000>Don't</font>**
    ```js
    careTakerList.map(async (careTaker) => {
        const newRCode = await genRecommendationCode();
        ...
    })
    ```

    **<font color=#008000>Do</font>**
    ```js
    for (careTaker of careTakerList) {
        const newRCode = await genRecommendationCode();
        ...
    }
    ```
    
<br/>

* It'd better use `for ... of` statement when the iteration returns nothing. Vice versa, it's recommended to use `map()` when the iteration returns something.

    **<font color=#b00000>Don't</font>**
    ```js
    const careTakerIdList = [];
    careTakerList.map((careTaker) => {
        careTakerIdList.push(careTaker._id);
    });
    ```

    **<font color=#008000>Do</font>**
    ```js
    const careTakerIdList = [];
    for (careTaker of careTakerList) {
        careTakerIdList.push(careTaker._id);
    }
    ```

    **<font color=#008000>Do</font>**
    ```js
    const newCareOrderList = careOrderList.map((careOrder) => {
        const commission = calculateCommission(careOrder);
        return {careOrder: careOrder, commission: commission}
    });
    ```

<br/>

* In many cases, handling `Promises` with `await` is preferred to handling with `then()`. Particularly, do not use concatenated `then()` since we cannot handle errors delicately.

    **<font color=#b00000>Don't</font>**
    ```js
    CareOrder.findById(careOrderId)
        .then(async (careOrder) => {
            return CareTaker.findByIdAndUpdate(
                careTakerId,
                {orderId: careOrder._id}
            );
        })
        .then((careTaker) => {
            return careTaker
        })
        .catch((error) => {
            ...
        });
    ```

    **<font color=#008000>Do</font>**
    ```js
    const careOrder = await CareOrder.findById(careOrderId)
        .catch((error) => {
            ...
        })

    if (!careOrder) { ... }

    const careTaker = await CareTaker.findByIdAndUpdate(
        careTakerId,
        {orderId: careOrder._id}
    )
        .catch((error) => {
            ...
        })

    if (!careTaker) { ... }
    ```

<br/>

* Be aware that `sort()` is an in-place function, so do not expect it to return a new sorted array.

    **<font color=#b00000>Don't</font>**
    ```js
    aggregatedJourneyList =
        aggregatedJourneyList.sort((a, b) => b._score - a._score);
    ```

    **<font color=#008000>Do</font>**
    ```js
    aggregatedJourneyList.sort((a, b) => b._score - a._score);
    ```

<br/>

* Be aware that some functions provided by `lodash` probably do not behave as you expect in some cases.

    **<font color=#b00000>Aware</font>**
    ```js
    _.isEmpty(123) // return true
    ```