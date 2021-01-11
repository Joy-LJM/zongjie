### BUG描述
- 在修改商品详情的时候，如果先修改商品名称、描述、数量等，然后再修改图片的话，会出现已修改等内容被重置为初始化等值;后来查了原因是因为在useEffect获取商品信息和useEffect表单信息初始化这里出了问题;在异步获取商品信息这里的第二个参数设置为空数组,让它只执行一次,而单信息初始化的第二个参数不传,是为了让在获取到商品信心后可以自动执行
useEffect(()=>{
    // 商品编辑的时候才执行获取商品详情
    if(id!=0) dispatch(getGoodDetailAction({id}))
    return undefined
  }, [])
useEffect(()=>{
    if(id!=0) form.setFieldsValue(info) // 表单赋值
return undefined
})
- 可以看到bug到原因是表单初始化执行了两次,第一次是在获取到商品信息后初始化,第二次是图片上传成功后,img的声明式变量src变了,变了之后,表单信息初始化的useEffect就重新执行.
- 我想要表单初始化只执行一次,可以设置一个声明式变量flag,用来表示编辑表单是否已经初始赋值:设置它的初始值为false,在表单赋值之前先进行flag判断,为false就进行赋值,把flase变为true,这样就不会二次赋值
useEffect(()=>{
    if(!flag) { // 编辑表单未赋初始值
      if(id!=0) form.setFieldsValue(info) // 表单赋值
      if(info._id) { setFlag(true) } // 编辑表单初始赋值完成，flag变为true
    }
    return undefined
  })
- bug2:先编辑提交商品信息后,如果在点击新增商品,这是商品表单会有初始值,这是不好的.原因就是点击编辑商品的时候,在redux中就有一个商品信息,如果编辑完提交后没有清掉,这个商品信息就会保留下来,所有有这个bug存在.只需要在编辑提交后做个清除的操作就行