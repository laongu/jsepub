# jsepub
thư viện tạo epub

```html
<script src="https://cdn.jsdelivr.net/gh/laongu/jsepub/jsepub.js"></script>
```

```typescript
// Import thư viện jszip
const JSZip = require('jszip');
const jsepub = new jsEpub();

jsepub.init({
  title: 'Tiêu đề sách',
  author: 'Tác giả sách',
  publisher: 'Nhà xuất bản sách',
  description: '<b>Mô tả</b> sách',
  tags: ['epub', 'tag']
});

// ảnh bìa
jsepub.cover('https://placehold.co/600x800/000000/FFFFFF.png');

// thêm chương
jsepub.addChapter('Chương 1', '<p>Nội dung chương 1.</p>');
jsepub.addChapter('Chương 1.1', '<p>Nội dung chương 1.1.</p>');
jsepub.addChapter('Chương 1.2', '<p>Nội dung chương 1.2.</p>');
jsepub.addChapter('Chương 2', '<p>Nội dung chương 2.</p>');
jsepub.addChapter('Chương 3', '<p>Nội dung chương 3.</p>');
jsepub.addChapter('Chương 3.1', '<p>Nội dung chương 3.1.</p>');
jsepub.addChapter('Chương 4', '<p>Nội dung chương 4.</p>');

jsepub.generate().then(epubBlob => {
  const downloadLink = document.createElement('a');
  downloadLink.href = URL.createObjectURL(epubBlob);
  downloadLink.download = `${jsepub.title}.epub`;
  document.body.appendChild(downloadLink);
  downloadLink.click();
  document.body.removeChild(downloadLink);
});
```
