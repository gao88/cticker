## cticker
circle time queue

## Demo
```
package cticker

import (
	"fmt"
	"testing"
	"time"
)

func TestCTicker(t *testing.T) {
	ticker := NewQueue(10, 0)
	for index := 0; index < 100; index++ {
		var i = index

		err := ticker.AddTimerTask(fmt.Sprint(index), func() {
			fmt.Println("1.index:", i)
		})

		if err != nil {
			fmt.Println(err)
		}
	}

	time.Sleep(time.Second * 5)

	for index := 0; index < 100; index++ {
		var i = index

		err := ticker.AddTimerTask(fmt.Sprint(index), func() {
			fmt.Println("2.index:", i)
		})

		if err != nil {
			fmt.Println(err)
		}
	}

	time.Sleep(time.Hour)
}
```