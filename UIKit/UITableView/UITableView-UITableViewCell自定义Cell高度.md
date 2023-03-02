# UITableView-UITableViewCell自定义Cell高度

## 设置TableViewCell的高度为自定义高度

``` swift

tableView.rowHeight = UITableView.automaticDimension

```

## 设置UITableViewCell的预估高度

``` swift

tableView.estimatedRowHeight = 100

```

## 通过约束自动撑开内容即可

这里以SnpKit为例

``` swift

contentView.addSubview(subTitleLabel)
subTitleLabel.snp.makeConstraints { make in
  make.left.equalTo(videoContentView.snp.right).offset(8)
  make.top.equalTo(titleLabel.snp.bottom).offset(4)
  make.right.equalTo(tipsView.snp.left).offset(-16)
  make.bottom.equalTo(-12)
}

```