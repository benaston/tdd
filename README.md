tdd
===

```C#

private PutApi _putApi;
private PostApi _postApi;
private MyType _typeUnderTest;

[SetUp]
public void SetUp() 
{
  _putApi = MockRepository.GenerateStub<PutApi>();
  _postApi = MockRepository.GenerateStub<PostApi>();
  _typeUnderTest = new MyType(_putApi, _postApi);
}

[Test]
public void UsesPostApiWhenNewPrice() 
{
  //...
}

[Test]
public void ShouldUsePostApiWhenNewPrice() 
{
  //...
}

[Test]
public void Save_NewPrice_UsesPostApi() 
{
  //arrange
  _putApi.Stub(d => d.MethodName(Arg<string>.Is.Anything)).Return("foo");
  
  //act
  _typeUnderTest.Save();
  
  //assert
  _postApi.AssertWasCalled(a => a.Save(Arg<string>.Is.Anything));
}

```
