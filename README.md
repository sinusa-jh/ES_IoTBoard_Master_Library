# ES_IoTBoard_Master_Library

## API Guide
<details>
<summary>RS485 데이터 수신 Function 및 Buffer 선언</summary>

```c
void sn_iot_set_char_to_buffer(uint8_t ch)
uint8_t _sn_iot_recv_buff[1024];
uint32_t _sn_iot_recv_buff_idx;
uint8_t _sn_uart_int_buff[2];
```

##### description
UART IT 사용을 위해 buffer 를 선언하고 HAL_UART_RxCpltCallback 함수내부에 Function 을 호출

##### Parameters

> | name      | data type               | description                                                           |
> |-----------|-------------------------|-----------------------------------------------------------------------|
> |uint8_t      |   uint8_t | Uart Rx Character  |

##### Return

> |data type               | description                                                           |
> |-------------------------|-----------------------------------------------------------------------|
> |void      |    |

##### Example

```c
uint8_t _sn_iot_recv_buff[1024] = {0, };
uint32_t _sn_iot_recv_buff_idx = 0;
uint8_t _sn_uart_int_buff[2] = {0, };
.
.
.
UART_HandleTypeDef huart1;
.
.
.

void HAL_UART_RxCpltCallback(UART_HandleTypeDef *huart)
{
	if (huart == &huart1) {
		sn_iot_set_char_to_buffer(_sn_uart_int_buff[0]);
		HAL_UART_Receive_IT(&huart1, _sn_uart_int_buff, 1);
	}
}


```


</details>



<details>
<summary>초기화</summary>

```c
uint8_t sn_iot_init(UART_HandleTypeDef *uart)
```

##### description
IoT Libaray 사용을 위한 초기화 수행

##### Parameters

> | name      | data type               | description                                                           |
> |-----------|-------------------------|-----------------------------------------------------------------------|
> |uart      |   UART_HandleTypeDef | Uart Handle  |

##### Return

> |data type               | description                                                           |
> |-------------------------|-----------------------------------------------------------------------|
> |uint8_t      |   If 0 : Success ,  else : Fail |

</details>

<details>
<summary>WiFi 접속</summary>

```c
void sn_iot_wifi_start(char *ssid, char* passphrase)
```

##### description
IoT Libaray 사용을 위한 초기화 수행

##### Parameters

> | name      | data type               | description                                                           |
> |-----------|-------------------------|-----------------------------------------------------------------------|
> |ssid      |   char * | 접속하고자 하는 AP 의 ssid  |
> |passphrase      |   char * | 접속하고자 하는 AP 의 passphrase  |

##### Return

> |data type               | description                                                           |
> |-------------------------|-----------------------------------------------------------------------|
> |void      |    |

</details>

<details>
<summary>WiFi 접속 확인</summary>

```c
bool sn_iot_is_wifi_connected()
```

##### description
AP 에 접속 상태 확인 

##### Parameters

> | name      | data type               | description                                                           |
> |-----------|-------------------------|-----------------------------------------------------------------------|
> | None     |   void |  |

##### Return

> |data type               | description                                                           |
> |-------------------------|-----------------------------------------------------------------------|
> |bool      |   If true : Success ,  else : Fail |

</details>

<details>
<summary>Mqtt 서버 접속 </summary>

```c
void sn_iot_mqtt_start()
```

##### description
IoT Mqtt Server 에 접속 시작

##### Parameters

> | name      | data type               | description                                                           |
> |-----------|-------------------------|-----------------------------------------------------------------------|
> | None     |   void |  |

##### Return

> |data type               | description                                                           |
> |-------------------------|-----------------------------------------------------------------------|
> |void      |    |

</details>

<details>
<summary>Mqtt 서버 접속 확인</summary>

```c
bool sn_iot_is_mqtt_connected()
```

##### description
Mqtt 서버 접속 결과 확인

##### Parameters

> | name      | data type               | description                                                           |
> |-----------|-------------------------|-----------------------------------------------------------------------|
> | None     |   void |  |

##### Return

> |data type               | description                                                           |
> |-------------------------|-----------------------------------------------------------------------|
> |bool      |   If true : Success ,  else : Fail |

</details>


