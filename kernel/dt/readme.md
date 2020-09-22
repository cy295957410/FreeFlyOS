## dt.c

主要功能：GDT和IDT表的建立和加载

1、GDT表在bootsector.S中就建立了，但那处于16位实模式下，而此时程序已进入32位保护模式，GDT每个段描述符限长变成4GB，所以需要建立一个新的GDT表，并加载到GDTR寄存器中。

2、IDT表和GDT表不同的是需要设置中断号和中断向量，并将硬件PIC上的中断号和中断向量绑定，当发生一个硬件中断时，比如按下键盘，PIC就会向系统送一个中断号（硬件完成），然后就会去IDT表中找该中断号对应的中断向量，然后执行相应的中断服务处理程序。

## dt.h

gdt和idt的属性设置