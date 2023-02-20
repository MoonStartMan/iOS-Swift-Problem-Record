# UITableView-侧滑删除

## 创建UITableView

``` swift

tableView = UITableView(frame: .zero, style: .grouped)
tableView.delegate = self
tableView.dataSource = self
tableView.register(SlidesCell.self, forCellReuseIdentifier: NSStringFromClass(SlidesCell.self))
tableView.backgroundColor = .clear
tableView.separatorStyle = .none

addSubview(tableView)
tableView.snp.makeConstraints { make in
	make.edges.equalToSuperview()
}

```

## 遵循UITableView协议完成侧滑删除

``` swift

func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
	return modelArray.count
}
    
func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
  guard let cell = tableView.dequeueReusableCell(withIdentifier: NSStringFromClass(SlidesCell.self), for: indexPath) as? SlidesCell else {
  	fatalError()
  }
  cell.model = modelArray[indexPath.item]
  cell.selectionStyle = .none
  return cell
}
    
/// 打开TableView 允许侧滑
func tableView(_ tableView: UITableView, canEditRowAt indexPath: IndexPath) -> Bool {
	return true
}
    
/// 侧滑样式
func tableView(_ tableView: UITableView, editingStyleForRowAt indexPath: IndexPath) -> UITableViewCell.EditingStyle {
	return .delete
}
    
/// 修改编辑按钮的文字
func tableView(_ tableView: UITableView, titleForDeleteConfirmationButtonForRowAt indexPath: IndexPath) -> String? {
	return "删除"
}

/// 删除操作
func tableView(_ tableView: UITableView, trailingSwipeActionsConfigurationForRowAt indexPath: IndexPath) -> UISwipeActionsConfiguration? {
	let deleteAction = UIContextualAction(style: .destructive, title: "delete") { [weak self] (contextualAction, view, completionHandler) in
      tableView.setEditing(false, animated: true)
      self?.modelArray.remove(at: indexPath.item)
      tableView.reloadData()
      completionHandler(true)
		}
    deleteAction.backgroundColor = .red
    deleteAction.image = UIImage(named: "list_delete_btn")
    let swipeActions = UISwipeActionsConfiguration(actions: [deleteAction])
	return swipeActions
}

```