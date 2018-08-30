# AtomicInteger

    // setup to use Unsafe.compareAndSwapInt for updates
    private static final Unsafe unsafe = Unsafe.getUnsafe();
    private static final long valueOffset;
    
     static {
            try {
                valueOffset = unsafe.objectFieldOffset
                    (AtomicInteger.class.getDeclaredField("value"));
            } catch (Exception ex) { throw new Error(ex); }
        }
        
valueOffset 逻辑内存地址




* AtomicInteger对象的getAndIncrement

         /**
             * Atomically increments by one the current value.
             *
             * @return the previous value
             */
            public final int getAndIncrement() {
                return unsafe.getAndAddInt(this, valueOffset, 1);
            }


* unsafe的getAndAddInt 循环+CAS

      public final int getAndAddInt(Object var1, long var2, int var4) {
            int var5;
            do {
                var5 = this.getIntVolatile(var1, var2);
            } while(!this.compareAndSwapInt(var1, var2, var5, var5 + var4));
    
            return var5;
        }
    
    
* unsafe的getIntVolatile

unsafe获取volatile的变量 下面的var2就是valueOffset var1就是AtomicInteger对象
    public native int getIntVolatile(Object var1, long var2);