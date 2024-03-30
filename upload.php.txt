<?php
$data = json_decode(file_get_contents('data.json'), true);

if ($_FILES['image'] && $_POST['text']) {
    $newData = [
        'image' => $_FILES['image']['name'],
        'text' => $_POST['text']
    ];

    $data[] = $newData;

    file_put_contents('data.json', json_encode($data));

    echo json_encode(['message' => 'Data uploaded successfully']);
} else {
    echo json_encode(['error' => 'Image or text is missing']);
}
?>
