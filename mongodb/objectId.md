# ObjectId
MongoDB 里的 _id 是 ObjectId 类型，一共 12 字节，由三部分组成：
- 4 字节表示时间戳
- 5 字节表示随机数
- 3 字节表示计数器

由于里面包含了时间戳，所以我们可以通过一些驱动提供的类似 Timestamp() 方法提取出前四字节的时间戳。

```go
// Timestamp extracts the time part of the ObjectId.
func (id ObjectID) Timestamp() time.Time {
	unixSecs := binary.BigEndian.Uint32(id[0:4])
	return time.Unix(int64(unixSecs), 0).UTC()
}
```