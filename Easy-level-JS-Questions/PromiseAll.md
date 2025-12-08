function myPromiseAll(promises) {
  return new Promise((resolve) => {
    const output = [];
    let done = 0;

    promises.forEach((p, index) => {
      p.then(value => {
        output[index] = value;
        done++;

        if (done === promises.length) {
          resolve(output);
        }
      });
    });
  });
}

const p1 = Promise.resolve(10);
const p2 = Promise.resolve(20);
const p3 = new Promise(res => setTimeout(() => res(30), 1000));

myPromiseAll([p1, p2, p3]).then(console.log);
