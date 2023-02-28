# -study--async-callback-with-Promise-



Promise 을 이용하여 비동기 callback이 완료된후 공통 처리
clickInit((resolve, checkedInput) => {
    //ajax나 기타 비동기처리
    setTimeout(function () {
        console.log('비동기처리');
        console.log('비동기처리1');
        console.log('비동기처리2');
        resolve();
    }, 2000)
});

function clickInit(callback) {
    document.querySelector('#btnClick').addEventListener('click', () => {
        new Promise((resolve) => {
            callback(resolve);
        }).then(() => {
            //완료후--------
            console.log('비동기 통신 완료후 공통처리--------------------');
            console.log('공통1');
            console.log('공통2');
            console.log('공통3');
        }).catch((err) => {
            //에러
            alert(err);
        });
    });
}
