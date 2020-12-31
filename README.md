stm32cubeide_printf


/* USER CODE BEGIN 4 */
#ifdef __GNUC__
#define PUTCHAR_PROTOTYPE int __io_putchar(int ch)
#else
  #define PUTCHAR_PROTOTYPE int fputc(int ch, FILE *f)
#endif /* __GNUC__ */

#define STR_SIZE 255

uint8_t str[STR_SIZE]={0};

PUTCHAR_PROTOTYPE
{
	static uint16_t index = 0 ;

	str[index++] = ch;
	if(ch=='\n')
	{
		HAL_UART_Transmit_DMA(&huart1,str,index);
		index = 0;
	}
	return ch;
}
/* USER CODE END 4 */
