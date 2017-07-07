## cticker
circle time queue

## Demo
package cticker

import (
	"fmt"
	"testing"
	"time"
)

func TestCTicker(t *testing.T) {
	ticker := NewQueue(10, 0)
	for index := 0; index < 10; index++ {
		var task Task
		var i = index

		task.handler = func() error {
			fmt.Println("1.index:", i)
			return nil
		}

		err := ticker.AddTimerTask(fmt.Sprint(index), &task)
		if err != nil {
			fmt.Println(err)
		}
	}

	time.Sleep(time.Second * 5)

	for index := 0; index < 100; index++ {
		var task Task
		var i = index

		task.handler = func() error {
			fmt.Println("2.index:", i)
			return nil
		}

		err := ticker.AddTimerTask(fmt.Sprint(index), &task)
		if err != nil {
			fmt.Println(err)
		}
	}

	time.Sleep(time.Hour)
}
