# interceptor
Magento2 Inteceptor-Fehler
Kategorien bei Magento2 geben den Fehler aus, dass diese schon existieren.

vendor/magento/framework/Data/Collection.php

line : 406

 public function addItem(\Magento\Framework\DataObject $item)
    {
        $itemId = $this->_getItemId($item);

        if ($itemId !== null) {
            if (isset($this->_items[$itemId])) {
                throw new \Exception(
                    'Item (' . get_class($item) . ') with the same ID "' . $item->getId() . '" already exists.'
               );
            }
            $this->_items[$itemId] = $item;
        } else {
            $this->_addItem($item);
        }
        return $this;
    }
become => below, wait for M2 fix
public function addItem(\Magento\Framework\DataObject $item)
{
$itemId = $this->_getItemId($item);

    if ($itemId !== null) {
        if (isset($this->_items[$itemId])) {
        return $this;
        }
        $this->_items[$itemId] = $item;
    } else {
        $this->_addItem($item);
    }
    return $this;
}
